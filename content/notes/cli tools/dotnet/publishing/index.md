---
title: notes > cli tools > dotnet > publishing
date: 2022-02-16T16:42:47-0700
draft: false 
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
- Framework-dependentincludes application and its dependencies. Users must install .NET runtime.
- Self-containedincludes application, its dependencies, .NET runtime, and libraries.

# Examples
<table>
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 12%" />
<col style="width: 11%" />
<col style="width: 11%" />
<col style="width: 35%" />
</colgroup>
<thead>
<tr class="header">
<th><p><strong>Framework-</strong></p>
<p><strong>dependent</strong></p>
<p><strong>executable</strong></p></th>
<th><p><strong>Self-</strong></p>
<p><strong>contained</strong></p>
<p><strong>executable</strong></p></th>
<th><p><strong>Cross-</strong></p>
<p><strong>platform</strong></p>
<p><strong>binary</strong></p></th>
<th><p><strong>Current</strong></p>
<p><strong>Platform</strong></p></th>
<th><p><strong>Specific</strong></p>
<p><strong>Platform</strong></p>
<p></p></th>
<th><strong>Command</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>X</td>
<td></td>
<td>X</td>
<td>X</td>
<td></td>
<td>dotnet publish</td>
</tr>
<tr class="even">
<td>X</td>
<td></td>
<td>X</td>
<td></td>
<td>X</td>
<td>dotnet publish -r &lt;RID&gt; --self-contained false</td>
</tr>
<tr class="odd">
<td></td>
<td>X</td>
<td></td>
<td></td>
<td>X</td>
<td>dotnet publish -r &lt;RID&gt;</td>
</tr>
</tbody>
</table>

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

# [Single File](https://docs.microsoft.com/en-us/dotnet/core/deploying/single-file#publish-a-single-file-app---cli)
```powershell
dotnet publish -p:PublishSingleFile=true --configuration Release --self-contained false --runtime win-x64
```
Single-file specific platform executable that does not require accompanying DLL file.

# Trim
Trimming reduces the size of compiled projects.
```powershell
dotnet publish … -p:PublishTrimmed=True # Assembly-level trimming.
dotnet publish … -p:publishTrimmed=True -p:TrimMode=link # Type-level and member-level trimming.
```
