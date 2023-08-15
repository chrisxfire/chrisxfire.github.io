---
title: dotnet
date: 2023-08-06T00:00:00-06:00
draft: false
weight: 1
---

# Overview
- Documentation: https://docs.microsoft.com/en-us/_net/core/tools/dotnet

# Compiling
`dotnet build` Build (compile) the executable for the app.

# Configuring
```powershell
dotnet <command> --diagnostics # Enable diagnostic output.
dotnet <command> --verbosity <level> # Levels are (q)uiet, (m)inimal, (n)ormal, (d)etailed, (diag)nostic.
dotnet new globaljson --sdk-version <ver> # Create a global.json file to target the .NET SDK version ver.
```
- The dotnet command searches the current directory and subdirectories for a `global.json` file, so this can be created in a subdirectory of the project.

# Getting Information
```powershell
dotnet --info # List information on .NET installation, machine environment, etc
dotnet --list-runtimes # List the installed .NET runtimes.
dotnet --list-sdks # List the installed .NET SDKs.
dotnet new --list # List currently installed templates.
```

# Maintenance Commands
```powershell
dotnet clean # Delete temporary files.
dotnet sdk check # Check versions of .NET SDKs and runtimes installed; warn if any are out of date.
```

# Managing Packages
```powershell
dotnet add package <package> # Download, install, and add package to project. Also updates a package.
                            --version <ver> # Optionally, use version of package.
dotnet list package # List installed packages.
                    --include-transitive # List installed packages and their dependencies.
                    --outdated # List outdated packages.
dotnet remove package <package> # Uninstall a package.
dotnet pack # Create a NuGet package for the project.
dotnet tool install <package> # Install a global package (tool).
dotnet new -i <package> # Install a template.
```

# Managing Projects
```powershell
dotnet new console # Create a new console project in the CWD.
                    -f FRAMEWORK # Create a new console project using framework version framework.
                    -o APPNAME # Create a new console project in subfolder APPNAME.
dotnet restore # Install dependencies for a new or cloned project.
```

# References
```powershell
dotnet add app/app.csproj reference lib/lib.csproj # Add lib/lib.csproj as a reference to app/app.csproj
dotnet add reference app/app.csproj # Add app/app.csproj as a reference to the project in the current directory
```

# Running Projects
```powershell
dotnet run # Build then run the project in the CWD.
            -- arg, … # Pass arg1 as a command line argument.
dotnet watch run # Start a file watch that runs a command when a file changes. Useful for hot reload in ASP.NET.
```

# Testing
```powershell
dotnet test # Run all discovered tests.
            --list-test # List all discovered tests.
```

# dotnet watch
A file watcher.  If the application supports hot reload, this command hot reloads the application whenever a code change is detected.  If not, it restarts the application.
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

# dotnet workload
```powershell
dotnet workload install <WORKLOAD_ID> # Install one or more workloads.
dotnet workload update Update all installed workloads.
dotnet workload list # List workloads available.
dotnet workload search <SEARCH_STRING> # Search for available workloads.
dotnet workload uninstall <WORKLOAD_ID> # Uninstall one or more workloads.
dotnet workload repair # Repair workload installations.
dotnet workload restore <PROJECT | SOLUTION> # Restore workloads required for a project.
```
