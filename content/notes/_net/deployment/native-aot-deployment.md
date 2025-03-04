---
title: native aot deployment
date: 2022-11-25T20:53:06-0700
draft: false
weight: 1
---

# overview
Publishing as Native AOT produces a self-contained app that has been ahead-of-time compiled into native code.

Advantages:
- Faster startup time
- Smaller memory footprint

Limitations:
- Availability: 
  - GA: .NET 7: Console applications only
  - Preview: ASP.NET Core 8 
- All [limitations of trimming](https://learn.microsoft.com/en-us/dotnet/core/deploying/trimming/incompatibilities) apply.
- All [limitations of single-file deployments](https://learn.microsoft.com/en-us/dotnet/core/deploying/single-file/overview?tabs=cli#api-incompatibility) apply.
- No dynamic loading (`Assembly.LoadFile`)
- No runtime code generation (`System.Reflection.Emit`)
- Apps include required runtime libraries (like all self-contained apps), so their size is larger than framework-dependent apps.

# requirements
- On Windows, Desktop Development w/C++ workload
- On Linux, clang, zlib1g-ev

# publishing
1. Update the project file:
    `SomeProject.csproj`  
    ```xml
    <PublishAot>true</PublishAot>
    ```
2. Publish the app for a specific runtime identifier:
    ```powershell
    dotnet publish -r <RUNTIME-IDENTIFIER> -c Release
    ```

# native libraries
This capability also allows for publishing .NET class libraries that can be consumed from non-.NET languages.

# AOT-Compatibility Analyzers
> [!IMPORTANT]
> Availability: .NET 8  

Use the `IsAotCompatible` property to provide analyzers for AOT compatibility:  
`SomeProject.csproj`  
```xml
<PropertyGroup>
    <IsAotCompatible>true</IsAotCompatible>
</PropertyGroup>
```
