---
title: single file deployment
date: 2023-07-17T00:00:00-06:00
draft: false
weight: 1
---

# overview
Single-file deployment bundles all application-dependent files into a single binary.  This deployment method is supported for both framework-dependent and self-contained apps.
- Documentation: https://learn.microsoft.com/en-us/dotnet/core/deploying/single-file/overview?tabs=cli 

# Publishing a Single-file App
1. Update the project file:  
   `csproj`
   ```xml
   <PropertyGroup>
        <PublishSingleFile>true</PublishSingleFile>
   </PropertyGroup>
   ```
2. Publish the app for a specific runtime identifier:
   ```powershell
   dotnet publish -r <runtime-identifier>
   ```

Alternatively, an app can be published as a single file without updating the project file:
```powershell
dotnet publish -r <runtime-identifier> -p:PublishSingleFile=true --self-contained <true|false>
```

# considerations
## excluding certain files
Update the project file:  
`csproj`
```xml
<ItemGroup>
    <Content Update="Plugin.dll">
        <!-- Copies the file to the Publish directory but does not include it 
             in the deployment: -->
        <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
        <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
    </Content>
</ItemGroup>
```

## including pdb files
Single-file apps have all related PDB files not bundled by default.  
To change this, update the project file:  
`csproj`
```xml
<PropertyGroup>
    <DebugType>embedded</DebugType>
</PropertyGroup>
```

## compress assemblies
Set the `EnableCompressionInSingleFile` property to `true`.  All embedded assemblies will be compressed.

Note: this has a performance cost.

## Inspecting Single-file Apps
Use [ILSpy](https://ilspy.net/).  This tool can inspect the contents of a single-file bundle.
