---
layout: post
title: "notes: building kubernetes v1.26.1 on debian 11/stable"
date: 
categories: notes
---
<style>
r { color: Red }
o { color: Orange }
g { color: Green }
b { color: Blue }
</style>
###### abstract
These are notes on how to build a Kubernetes cluster of 3 nodes (one control plane node, two worker nodes) on a fresh install of Debian 11 (stable):
* Control plane (alpha) — 192.168.86.10
* Worker #1 (bravo) — 192.168.86.11
* Worker #2 (charlie) — 192.168.86.12

Credit:  These notes use a [guide][pradeeps-guide] written by Pradeep Kumar as a starting point and provides updates for Kubernetes v1.26.

# set hostnames
On the specified node:
```bash
sudo hostnamectl set-hostname alpha # on alpha
sudo hostnamectl set-hostname bravo # on bravo
sudo hostnamectl set-hostname charlie # on charlie
```

Configure `/etc/hosts` on all nodes:
```
127.0.0.1 localhost  
192.168.86.10 alpha alpha.lan  
192.168.86.11 bravo bravo.lan  
192.168.86.12 charlie charlie.lan
```

# disable swap
On all nodes:
```bash
sudo swapoff -a
```
Edit `/etc/fstab`:
* Look for the line contains `swap` (on a default Debian 11 installation, it is prefixed with a line that reads "swap was on [path] during installation"
* Comment that line out.

# firewall
If you've enabled `ufw`, either:
1. disable it on all nodes:
	```bash
	sudo ufw stop
	sudo ufw disable
	```
2. add allow rules for k8s:
	1. On control plane:
		```bash
		sudo ufw allow 6443/tcp
		sudo ufw allow 2379/tcp
		sudo ufw allow 2380/tcp
		sudo ufw allow 10250/tcp
		sudo ufw allow 10251/tcp
		sudo ufw allow 10252/tcp
		sudo ufw allow 10255/tcp
		sudo ufw reload
		```
	1. On worker nodes:
		```bash
		sudo ufw allow 10250/tcp
		sudo ufw allow 3000:32767/tcp
		sudo ufw reload
```

# kernel parameters (all nodes)
### set kernel parameters for containerd
Create a file under `/etc/modules-load.d` so these parameters are applied on every boot:
```bash
cat <<EOF | sudo tee /etc/modules-load.d/containerd.conf
overlay
br_netfilter
EOF
```

Apply the parameters now:
```bash
sudo modprobe overlay # enable overlay2 storage driver
sudo modprobe br_netfilter # enable transparent masquerading and facilitate VxLAN traffic
```

### enable packet forwarding
```bash
cat <<EOF | sudo tee /etc/sysctl.d/99-kubernetes-k8s.conf
net.bridge.bridge-nf-call-iptables = 1 # enable sending packets that cross bridge to iptables
net.bridge.bridge-nf-call-ip6tables = 1 # same for ipv6
net.ipv4.ip_forward = 1 # enable forwarding packets meant for other destinations
EOF
```
```bash
sudo sysctl --system # apply the above changes immediately
```

# containerd (all nodes)
Kubernetes v1.26+ [no longer supports containerd versions 1.5 or earlier][containerd-versions].  Debian 11 (stable) comes with version 1.4.13 at the time of this writing.  Get version 1.6+ from Debian's unstable branch.

### define the default release
So that *all* packages do not get upgraded to unstable:
```bash
sudo touch /etc/apt/apt.conf.d/default-release
sudo echo 'APT::Default-Release "stable" >> /etc/apt/apt.conf.d/default-release'
```

### add unstable to apt sources
```bash
sudo echo 'deb https://deb.debian.org/debian/ unstable main contrib' >> /etc/apt/sources.list
sudo echo 'deb-src https://deb.debian.org/debian/ unstable main contrib' >> 
```

### install containerd
```bash
sudo apt update
sudo apt install -t unstable containerd -y
```

### configure containerd
Set `containerd`'s default config:
```bash
containerd config default | sudo tee /etc/containerd/config.toml >/dev/null 2>&1 # load the config in this file and send errors to /dev/null
```

Configure `containerd` to use systemd to manage Linux cgroups:
```bash
sudo nano /etc/containerd/config.toml
```
* In `/etc/containerd/config.toml`, find the section with this header: `[plugins."io.containerd.grpc.v1.cri".containerd.runtimes.runc.options]`
* Underneath that section header, add this line:
* `SystemdCgroup = true`*
* Close and save the file.

![cgroups](https://github.com/chrisxfire/chrisxfire.github.io/assets/cgroups.png) 

Restart containerd
```bash
sudo systemctl restart containerd
sudo systemctl enable containerd # make sure it's enabled to start on each launch
```

# install kubernetes (all nodes)
Download packages, configure sources:
```bash
# download the required packages:
sudo apt install gnupg gnupg2 curl software-properties-common -y
# get the kubernetes repo apt key and place it in the trusted.gpg.d directory:
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/cgoogle.gpg
# add the kubernetes repo to apt repos list:
sudo apt-add-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main"
```

Install kubernetes:
```bash
sudo apt update # required now that you've added the kubernetes repo
sudo apt install kubelet kubeadm kubectl -y
sudo apt-mark hold kubelet kubeadm kubectl # exclude all kubernetes packages from upgrades
```

# build a kubernetes cluster
### control plane node
Initialize the control plane:
```bash
sudo kubeadm init --control-plane-endpoint=alpha
```
Look for output that reads "Your kubernetes control-plane has initialized successfully!"  Make note of the line that starts with `kubeadm join alpha:6443` as this is the line you'll use to join worker nodes to the cluster.

Configure the control plane:
```bash
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config # copy admin.conf as config to kubernetes' directory
sudo chown $(id -u):$(id -g) $HOME/.kube/config # take ownership of that config
```

Check the cluster:
```bash
kubectl get nodes
kubectl cluster-info
```

### worker nodes
Join the worker nodes to the cluster:
```bash
sudo kubeadm join alpha:6443 --token <token> --discovery-token-ca-cert-hash <hash>
```

### control plane node
Confirm the worker nodes have joined the cluster
```bash
kubectl get nodes
```

# calico pod network addon (control plane node)
Apply Calico:
```bash
kubectl apply -f https://projectcalico.docs.tigera.io/manifests/calico.yaml
```

if `ufw` is enabled, open ports for Calico:
```bash
sudo ufw allow 179/tcp
sudo ufw allow 4789/udp
sudo ufw allow 51820/udp
sudo ufw allow 51821/udp
```

Verify the Calico pods:
```bash
kubectl get pods -n kube-system
```
![get-pods](https://github.com/chrisxfire/chrisxfire.github.io/assets/get-pods.png)

Verify the nodes:
![get-nodes](https://github.com/chrisxfire/chrisxfire.github.io/assets/get-nodes.png)
[containerd-versions]: https://kubernetes.io/blog/2022/11/18/upcoming-changes-in-kubernetes-1-26/#cri-api-removal
[pradeeps-guide]: https://www.linuxtechi.com/install-kubernetes-cluster-on-debian/

All set.