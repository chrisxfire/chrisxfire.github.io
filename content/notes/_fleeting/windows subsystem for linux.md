---
title: windows subsystem for linux
date: 2025-02-23T00:00:00-06:00
draft: true
weight: 1
tags:
 - 
---

# [overview](https://learn.microsoft.com/en-us/windows/wsl/)
Windows Subsystem for Linux (WSL) is a Windows feature that runs Linux on Windows. 
In WSL v2, it runs a Linux distribution in a lightweight purpose-built virtual machine.

See also: https://learn.microsoft.com/en-us/linux

# installation
```powershell
wsl --install # with no argument, install Ubuntu by default
    --no-launch # do not launch the distribution after installing
    --no-distribution # do not install a distribution, just install WSL
```

Install WSL with another distribution, or install an additional distribution:
```powershell
wsl --install --distribution <distribution> # install <distribution>
```

Uninstall a distribution:
```powershell
wsl --unregister <distribution name> # this will uninstall the distribution and remove it from WSL's list of available distributions
```

# managing WSL
Set WSL version:
```powershell
wsl --set-version <distribution name> <1 | 2>
```

Set default WSL version:
```powershell
wsl --set-default-version <1 | 2>
```

Check status:
```powershell
wsl --status
```

Update:
```powershell
wsl --update
```

Shutdown:
```powershell
wsl --shutdown
```

# managing distributions
List available distributions:
```powershell
wsl --list --online
```

List installed distributions:
```powershell
wsl --list --verbose
```

Set default distribution:
```powershell
wsl --set-default <distribution name>
```

Start a distribution:
```powershell
<distribution name>
```

Stop a distribution:
```powershell
wsl --terminate <distribution name>
```

Change the default user for a distribution:
```powershell
<distribution name> config --default-user <user name>
```

Export a distribution to a distribution file:
```powershell
wsl --export <distribution name> <path> # exports to a tar file
                                  --vhd # exports to a vhd file (requires WSL 2)
```

Import a distribution
```powershell
wsl --import <distribution name> <install location> <path> [--vhd]
```

# [running linux GUI apps](https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps)
WSL 2 enables Linux GUI applications to feel native and natural to use on Windows.
- Launch Linux apps from the Windows Start menu
- Pin Linux apps to the Windows task bar
- Use alt-tab to switch between Linux and Windows apps
- Cut + Paste across Windows and Linux apps

## pre-requisite
Install a vGPU driver:
- [Intel](https://www.intel.com/content/www/us/en/download/19344/intel-graphics-windows-dch-drivers.html)
- [AMD](https://www.amd.com/en/support)
- [NVIDIA](https://www.nvidia.com/Download/index.aspx?lang=en-us)

