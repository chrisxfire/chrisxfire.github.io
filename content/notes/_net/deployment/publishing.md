---
title: publishing
date: 2022-02-16T16:42:47-0700
draft: false 
weight: 1
---
# [Publishing](https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-publish)
```powershell
dotnet publish [options] <proj|sltn> # Publish the application and its dependencies for hosting.
--arch <x64|x86 # Specify the target architecture. Don't use `--runtime`.
--configuration Debug|Release
--framework net6.0|net5.0|… # Specify the target .NET framework.
--output <path # Specify the output directory.
--self-contained <true|false> # Publish the .NET runtime with the application. Use with `--runtime`.
--runtime <RID> # Specify the target runtime environment. Use with `--self-contained`.
```
RIDs: `win-x64`, `win10-x64`, `win-x86`, `linux-x64`, `rhel-x64`
```powershell
--verbosity <level> # Levels are (q)uiet, (m)inimal, (n)ormal, (d)etailed, (diag)nostic.
```
Publishing modes:
- Framework-dependent — includes application and its dependencies. Users must install .NET runtime.
- Self-contained — includes application, its dependencies, .NET runtime, and libraries.

| Framework-dependent executable | Self-contained executable | Cross-platform binary | Current Platform | Specific Platform | Command                                          |
| ------------------------------ | ------------------------- | --------------------- | ---------------- | ----------------- | ------------------------------------------------ |
| X                              |                           | X                     | X                |                   | dotnet publish                                   |
| X                              |                           | X                     |                  | X                 | dotnet publish -r \<RID\> --self-contained false |
|                                | X                         |                       |                  | X                 | dotnet publish -r \<RID\>                        |

# No platform-specific executable
Add this to the project file:  
`<UseAppHost>False</UseAppHost>`

# PDB Files
PDB files are used to debug exceptions.
You can choose not to include them with the deployment. Save them if so.

# [ReadyToRun](https://docs.microsoft.com/en-us/dotnet/core/deploying/ready-to-run)
ReadyToRun images improve startup time but are larger in size.
ReadyToRun requires targeting a specific runtime environments.
```powershell
dotnet publish --configuration Release --runtime <RID> -p:PublishReadyToRun=true
```
Self-contained specific platform executable, ReadyToRun.

# Trim
Trimming reduces the size of compiled projects.
```powershell
dotnet publish … -p:PublishTrimmed=True # Assembly-level trimming.
dotnet publish … -p:publishTrimmed=True -p:TrimMode=link # Type-level and member-level trimming.
```
