---
title: overview
date: 2024-12-14T00:00:00-06:00
draft: false
weight: -1
tags:
 - kb/dotnet/dotnet-sdk
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/core/sdk)
The .NET SDK is a set of libraries and tools used to create .NET apps. It consists of:
- The .NET CLI
- The .NET runtime and libraries
- The `dotnet` driver
  - This tool:
    1. Runs framework-dependent apps
    2. Executes a command

# environment variables
More information: [.NET runtime environment variables](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-environment-variables#net-runtime-environment-variables)  
More information: [.NET SDK and CLI environment variables](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-environment-variables#net-sdk-and-cli-environment-variables)  

# [`dotnet-install` scripts](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-install-script)
[`dotnet-install.ps1`](https://dot.net/v1/dotnet-install.ps1) (Windows) and [`dotnet-install.sh`](https://dot.net/v1/dotnet-install.sh) (MacOS/Linux) are used to install the .NET SDK and shared runtime.

# [global.json](https://learn.microsoft.com/en-us/dotnet/core/tools/global-json)
The *global.json* file defines which .NET SDK version to use when executing .NET CLI commands.

# [Telemetry](https://learn.microsoft.com/en-us/dotnet/core/tools/telemetry)
The .NET SDK collects various telemetry and sends it to Microsoft. Some of this telemetry can be viewed at https://dotnet.microsoft.com/platform/telemetry.

## opting out
To opt out of .NET SDK telemetry collection, set the `DOTNET_CLI_TELEMETRY_OPTOUT` environment variable to `1` or `true`.