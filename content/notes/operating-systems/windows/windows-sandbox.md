---
title: windows sandbox
date: 2023-07-02T00:00:00-06:00
draft: false
weight: 1
---

# overview
A virtualized instance of Windows to run applications in isolation ("sandboxed" from the host machine).
- Documentation: https://learn.microsoft.com/en-us/windows/security/application-security/application-isolation/windows-sandbox/windows-sandbox-overview

# installing
From Administrator PowerShell:
```powershell
Enable-WindowsOptionalFeature -FeatureName "Containers-DisposableClientVM" -All -Online
```

Search for **Windows Sandbox** in start menu.
