---
title: trimming
date: 2023-07-24T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Assembly trimming removes unused parts of libraries from the application package, thereby reducing size.

Trimming is <u>only available for self-contained deployments</u>.

# Considerations
<o>Trimming has known incompatibilities.</o>  See https://learn.microsoft.com/en-us/_net/core/deploying/trimming/incompatibilities

# Enabling
To enable trimming:  
1. Enable trimming in the project file:   
    `SomeProject.csproj`
    ```xml
    <PropertyGroup>
        <PublishTrimmed>true</PublishTrimmed>
    </PropertyGroup>
    ```
2. Publish the app as self-contained
   - Via CLI:  
    ```powershell
    dotnet publish -r <RUNTIME-ID>
    ```
    Note: The `-p:PublishTrimmed=true` switch is not required if trimming is enabled in the project file.
   - Via Visual Studio:  
     1. **Right-click** project in Solution Explorer > **Publish**
     2. **More actions** > **Edit** 
     3. *Profile settings* dialog > Set the **Deployment mode** > Set the **Target runtime** > Check **Trim unused code** > **Save**
     4. **Publish** 

# Trimming Options
The following MSBuild properties and items change trimming behavior.  
Note: *ILLink* is the name of the underlying tool that implements trimming.

### Trim Mode
The default trim mode in .NET 7 is `full`.  This trims all assemblies:
```xml
<TrimMode>partial</TrimMode>
```

### Set trimmable assemblies
If the above is set to `partial`, set this to opt-in individual assemblies:
```xml
<ItemGroup>
    <TrimmableAssembly Include="ASSEMBLY-NAME" />
</ItemGroup>
```

### Root assemblies
Assemblies that are not trimmed is considered "rooted."  Additional assemblies can be rooted:
```xml
<ItemGroup>
    <TrimmerRootAssembly Include="ASSEMBLY-NAME" />
</ItemGroup>
```

### Analysis warnings
- `SuppressTrimAnalysisWarnings` is boolean if trim analysis warnings should be enabled.  Default = `false`. 
- `EnableTrimAnalyzer` is boolean to enable a limited set of Roslyn analyzers. Default = `true`.
- `ILLinkTreatWarningsAsErrors` is boolean to treat warnings as errors.
- `TrimmerSingleWarn` is boolean to show detailed errors instead of collapsing them into a single warning per assembly.
- `TrimmerRemoveSymbols` is boolean to remove symbols (such as PDBs) from the trimmed application.

# Framework Features Automatically Disabled When Trimming
See: https://learn.microsoft.com/en-us/_net/core/deploying/trimming/trimming-options?pivots=dotnet-7-0#framework-features-disabled-when-trimming

# Preparing a Library for Trimming
See https://learn.microsoft.com/en-us/_net/core/deploying/trimming/prepare-libraries-for-trimming

# Trimming Framework Library Features
See: https://learn.microsoft.com/en-us/_net/core/deploying/trimming/trimming-options?pivots=dotnet-7-0#trimming-framework-library-features
