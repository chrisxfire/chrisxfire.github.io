---
title: overview
date: 2023-05-30T00:00:00-06:00
draft: false
weight: -1
---

# Overview
- Tools are CLI apps installed from NuGet packages.  
- Tools are managed and used with the `dotnet tool` command.
- Documentation: https://learn.microsoft.com/en-us/dotnet/core/tools/

# Installing
```powershell
dotnet tool install <package_name>
    --global # install the tool globally
    --local # install the tool locally
```

# Diagnostic tools
| Tool            | Use                                                                                             |
| --------------- | ----------------------------------------------------------------------------------------------- |
| dotnet-counters | for first-level health monitoring and performance investigation                                 |
| dotnet-dump     | for collecting and analyzing Windows and Linux core dumps without a native debugger             |
| dotnet-gcdump   | for collecting garbage collector dumps of live .NET processes                                   |
| dotnet-monitor  | for monitoring .NET applications in production environments and to collect diagnostic artifacts |

## dotnet-monitor
| Subcommand                 | Description                                                                                    |
| -------------------------- | ---------------------------------------------------------------------------------------------- |
| dotnet-monitor collect     | Monitor an application, collect diagnostic artifacts, and send them to a specified destination |
| dotnet-monitor config show | Shows dotnet-monitor's current configuration                                                   |
| dotnet-monitor generatekey | Generate an API key and hash for HTTP authentication                                           |
