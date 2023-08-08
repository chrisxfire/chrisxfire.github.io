---
title: upgrade instructions
date: 2023-06-19T00:00:00-06:00
draft: false
weight: 1
---

# Performing Debian Major Version Upgrade
## 1. Upgrade the current system
```bash
sudo apt update
sudo apt full-upgrade -y
sudo apt autoremove
sudo systemctl reboot
```

## 2. Update configuration to the new codename
1. In `/etc/apt/sources.list`, change the Debian codename from the old codename to the new codename
2. In `/etc/apt/sources.list`, comment out `<old-codename>-backports` 

## 3. Upgrade to the new system
```bash
sudo apt update
sudo apt full-upgrade -y
sudo apt autoremove
sudo systemctl reboot
```

## 4. Confirm the new system is functional
```bash
sudo systemctl status
```

## 5. Restore backports
In `/etc/apt/sources.list`, uncomment `<old-codename>-backports` and replace `<old-codename>` with `<new-codename>`
