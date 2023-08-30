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

## dotnet-httprepl
See [notes on HttpRepl]({{< ref "../../../../asp.net/api/testing-with-httprepl" >}})

## dotnet-monitor
| Subcommand                 | Description                                                                                    |
| -------------------------- | ---------------------------------------------------------------------------------------------- |
| dotnet-monitor collect     | Monitor an application, collect diagnostic artifacts, and send them to a specified destination |
| dotnet-monitor config show | Shows dotnet-monitor's current configuration                                                   |
| dotnet-monitor generatekey | Generate an API key and hash for HTTP authentication                                           |

# Other Tools
## dotnet-openapi
Manages OpenAPI references in a project.  
Package: `microsoft.dotnet-openapi`

### Subcommands
The `Add` subcommands add an OpenAPI reference to the project file:
```xml
<OpenAPiReference Include="openapi.json" />
```

#### `add <file>`
```powershell
dotnet openapi add file
    [-p project] # the project to operate on
    [-c nswagcsharp|nswagtypescript] # the code generator to apply to the reference; defaults to nswagcsharp
    <file> # like ./OpenAPI.json 
```

#### `add <url>`
```powershell
dotnet openapi add url
    [-p project] # the project to operate on
    [-o <output-file>] # where to store the local copy of the OpenAPI file
    [-c nswagcsharp|nswagtypescript] # the code generator to apply to the reference; defaults to nswagcsharp
    <url> # like https://www.example.com/openapi.json 
```

#### `remove`
Deletes the OpenAPI reference. Clients will not be generated.
```powershell
dotnet openapi remove 
    [-p project] # the project to operate on
    <file> # like ./OpenAPI.json
```

#### `refresh`
Refresh the local file with the latest content from the URL:
```powershell
dotnet openapi refresh
    [-p project] # the project to operate on
    <url> # like https://www.example.com/openapi.json 
```

