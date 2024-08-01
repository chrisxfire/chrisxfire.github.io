---
title: berkeley packet filter
date: 2023-06-24T00:00:00-06:00
draft: false
weight: 1
---

# Berkeley Packet Filter (BPF)
- Provides a raw interface to netlayer 2, bypassing kernel
- Allows userland process to filter packets; BPF returns only those packets; other packets not copied from kernel to this process
- BPF = this filter + raw interface

# BPF Raw Datalink Interface
- Pseudo-devices taht bind to network interfaces
- READ retrieves buffers full of packets received on the interface
- WRITE injects packets on the interface

# Extended BFP (eBPF) (2014)
- Enables running sandboxed apps in privileged context
- This extends capabilities of kernel without changes to kernel source or loading kernel modules

## Uses
- High-throughput load balancers
- Cluster networking
- Security / DDoS protection
- Observability

# Express Data Path (XDP) (2016)
- eBPF-based technology to send and receive packets at high rates by bypassing most of the OS network stack
- Works by adding a hook in the receiving path of the kernel and letting a userland eBPF app decide the disposition of the packet
- The hook sits in the NIC driver just after interrupt and before `malloc` for the network stack
- XDP can drop 26M packets per second per core
- The eBPF app can be offloaded to NICs that support running such apps
- The eBPF app inspects the packet and returns:
  - `XDP_PASS` — pass the packet onto the network stack
  - `XDP_DROP` — silently drop the packet
  - `XDP_ABORTED` — drop the packet with an exception
  - `XDP_TX` — bounce the packet back to the same NIC it was received on
  - `XDP_REDIRECT` — bounce the packet to another NIC or userland socket
