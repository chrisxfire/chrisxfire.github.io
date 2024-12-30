---
title: trimming
date: 2023-07-24T00:00:00-06:00
draft: false
weight: 1
---

# overview
Assembly trimming removes unused parts of libraries from the application package, thereby reducing size.

Trimming is <u>only available for self-contained deployments</u>.

# considerations
<o>Trimming has known incompatibilities.</o>  See https://learn.microsoft.com/en-us/dotnet/core/deploying/trimming/incompatibilities

# enabling
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

# trimming options
The following MSBuild properties and items change trimming behavior.  
Note: *ILLink* is the name of the underlying tool that implements trimming.

### trim mode
The default trim mode in .NET 7 is `full`.  This trims all assemblies:
```xml
<TrimMode>partial</TrimMode>
```

### set trimmable assemblies
If the above is set to `partial`, set this to opt-in individual assemblies:
```xml
<ItemGroup>
    <TrimmableAssembly Include="ASSEMBLY-NAME" />
</ItemGroup>
```

### root assemblies
Assemblies that are not trimmed is considered "rooted."  Additional assemblies can be rooted:
```xml
<ItemGroup>
    <TrimmerRootAssembly Include="ASSEMBLY-NAME" />
</ItemGroup>
```

### analysis warnings
- `SuppressTrimAnalysisWarnings` is boolean if trim analysis warnings should be enabled.  Default = `false`. 
- `EnableTrimAnalyzer` is boolean to enable a limited set of Roslyn analyzers. Default = `true`.
- `ILLinkTreatWarningsAsErrors` is boolean to treat warnings as errors.
- `TrimmerSingleWarn` is boolean to show detailed errors instead of collapsing them into a single warning per assembly.
- `TrimmerRemoveSymbols` is boolean to remove symbols (such as PDBs) from the trimmed application.

# framework features automatically disabled when trimming
See: https://learn.microsoft.com/en-us/dotnet/core/deploying/trimming/trimming-options?pivots=dotnet-7-0#framework-features-disabled-when-trimming

# preparing a library for trimming
See https://learn.microsoft.com/en-us/dotnet/core/deploying/trimming/prepare-libraries-for-trimming

# trimming framework library features
See: https://learn.microsoft.com/en-us/dotnet/core/deploying/trimming/trimming-options?pivots=dotnet-7-0#trimming-framework-library-features
