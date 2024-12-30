---
title: central-package-management
date: 2023-07-23T00:00:00-06:00
draft: false
weight: 1
---

# overview
> [!IMPORTANT]
> Availability: NuGet v6.2  

Use to manage common dependencies across many different projects.

# enabling
1. Create a `Directory.Package.props` file at the root of the repository.
2. Enable central package management:
    `Directory.Package.props`  
    ```xml {hl_lines=[3,4,5]}
    <Project>
        <PropertyGroup>
            <ManagePackageVersionsCentrally>
                true
            <ManagePackageVersionsCentrally>
        </PropertyGroup>
    </Project>
    ```
3. For each package, define the package version required for your projects:
    ```xml
    <ItemGroup>
        <PackageVersion Include="PACKAGE.NAME" Version="X.Y.Z" />
    </ItemGroup>
    ```
4. For each project, define a package reference:
    ```xml
    <ItemGroup>
        <PackageReference Include="PACKAGE.NAME" />
    </ItemGroup>
    ```

# overriding package versions
- `PackageReference` elements can override the version specified in `PackageVersion` elements with the `VersionOverride` property.
- This feature can be disabled in `Directory.Packages.props` by setting `CentralPackageVersionOverrideEnabled` to `false`.

# global package references
Used to specify that a package will be used by every project in the repository:  
`Directory.Packages.props`
```xml
<Project>
    <ItemGroup>
        <GlobalPackageReference Include="PACKAGE.NAME" Version="X.Y.Z" />
    </ItemGroup>
</Project>
```

# considerations
- Only one `Directory.Package.props` file is evaluated for a given project.
  - The file closest to the project's directory is evaluated. 
