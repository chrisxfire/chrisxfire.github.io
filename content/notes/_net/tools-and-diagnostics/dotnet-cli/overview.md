---
title: overview
date: 2024-12-14T00:00:00-06:00
draft: false
weight: -1
tags:
 - kb/dotnet/dotnet-cli
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/core/tools/)
The .NET CLI is a cross-platform toolchain for developing, building, running, and publishing .NET apps.

At the heart of the toolchain is the `dotnet` driver, responsible for running framework-dependent apps or executing a command.

Commands follow this general structure: `dotnet <command> [option] [argument]`

# cli commands
## basic commands
- [`dotnet new`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-new) — creates a new project, configuration file, or solution.
- [`dotnet restore`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-restore) — restores the dependencies and tools of a project.
- [`dotnet build`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-build) — builds a project and its dependencies.
- [`dotnet publish`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-publish) — publishes the app and its dependencies to a folder for deployment to a hosting system.
- [`dotnet run`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-run) — runs source code.
- [`dotnet test`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-test) — executes unit tests.
- [`dotnet vstest`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-pack) — packs code into a NuGet package.
- [`dotnet clean`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-clean) — cleans the output of a project.
- [`dotnet sln`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-sln) — lists or modifies the projects in a .NET solution file.
- [`dotnet store`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-store) — stores assemblies in the runtime package store.
- [`dotnet watch`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-watch) — when changes in source code are detected, either restart, hot reload, or run a specified dotnet command.
- [`dotnet format`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-format) — formats code to match EditorConfig settings.

## project management commands
- `list|add|remove package`
- `list|add|remove reference`

## nuget package management commands

## [Workload management commands](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-workload)
- `workload clean` — clean up workload packs leftover from .NET SDK/Visual Studio updates where installation records for the pack no longer exist
  - `--all` — more aggressive; cleans every pack of the current SDK workload installation type
- `workload install <WORKLOAD_ID>` — Install one or more workloads.
- `workload list` — List workloads available.
- `workload repair` — Repair workload installations.
- `workload restore <PROJECT | SOLUTION>` — Restore workloads required for a project.
- `workload search <SEARCH_STRING>` — Search for available workloads.
- `workload uninstall <WORKLOAD_ID>` — Uninstall one or more workloads.
- `workload update` — Update all installed workloads.

## tool management commands
.NET tools are NuGet packages that contain console applications.

More notes: [tools](./tools/overview.md)

More information: https://learn.microsoft.com/en-us/dotnet/core/tools/global-tools

## advanced commands
- [`sdk check`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-sdk-check) — lists the latest available version of the .NET SDK and .NET runtime for each feature band.
- [`msbuild`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-msbuild) — allows access to an MSBuild. Running `dotnet msbuild -restore` is equivalent to `dotnet build`.
- [`build-server`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-build-server) — manages build servers.
- [`dev-certs`](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-dev-certs) — generates a self-signed certificate to enables HTTPS use in development.

# commonly used commands
## getting information
```powershell
dotnet --info # List information on .NET installation, machine environment, etc
dotnet --list-runtimes # List the installed .NET runtimes.
dotnet --list-sdks # List the installed .NET SDKs.
dotnet new --list # List currently installed templates.
```
