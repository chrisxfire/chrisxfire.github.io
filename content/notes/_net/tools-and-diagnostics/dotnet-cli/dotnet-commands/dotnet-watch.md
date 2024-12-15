---
title: dotnet watch
date: 2024-12-14T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/dotnet/dotnet-cli/dotnet-watch
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-watch)
`dotnet watch` is a file watcher.  If the application supports hot reload, this command hot reloads the application whenever a code change is detected.  If not, it restarts the application.
- `dotnet watch` can run any command dispatched via the `dotnet` executable.  If you can run `dotnet COMMAND`, you can run `dotnet watch COMMAND`.
- While `dotnet watch` is running, you can force a restart from the shell with <kbd>Ctrl</kbd>+<kbd>R</kbd>.
- Arguments passed after `--` are sent to the child `dotnet` process.  If running `dotnet watch run`, these arguments are options for `dotnet run`.

## Options
- `--list` — list all discovered files 
- `--no-hot-reload` — watch, but do not hot reload on change
- `--non-interactive` — prevent console input from being requested

## Files Watched by Default
All items in the `Compile`, `EmbeddedResource`, and `Watch` groups of the project file that match these glob patterns:
- `**/*.cs`
- `*.csproj`
- `**/*.resx`
- `wwwroot/**` 

To add or remove watched files:
`SomeProject.csproj`
```xml
<ItemGroup>
    <Watch Include="**\*.js" 
           Exclude="bin\**\*" />
</ItemGroup>
```