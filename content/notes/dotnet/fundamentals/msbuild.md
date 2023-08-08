---
title: msbuild
date: 2023-03-14T21:16:15-0600
draft: false
weight: 1
---
# [MSBuild](https://learn.microsoft.com/en-us/visualstudio/msbuild/msbuild?view=vs-2022)
- Runs build processes to build apps.
- Used by Visual Studio to build.
- Used by `dotnet build` to build.

## Project (.proj) Files
- XML-based

# [Properties](https://learn.microsoft.com/en-us/visualstudio/msbuild/msbuild-properties?view=vs-2022)
Key-value pairs used to configure builds.

Always inside a `<PropertyGroup>` tag:
```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

## Conditionals
```xml
<SomeProperty Condition="condition">DefaultValue</SomeProperty>
```

# [Items](https://learn.microsoft.com/en-us/visualstudio/msbuild/msbuild-items?view=vs-2022)
Inputs into the build system; usually files.
- Grouped into item types based on user-defined item names.
- Item types are used in tasks which use the individual items to perform the steps of the build process.

An item type named Compile that includes two files:
```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```
## Referencing Item Types
Use `@(ItemType)`

# Tasks
Executable code that MSBuild projects use to perform build operations.
- Can be re-used
- Can be shared across projects

Tasks are children of a `Target` element. They accept parameters which are passed as attributes to the element:
```xml
<Target Name="SomeTask">
    <TaskAction TaskParameter="value" />
</Target>
```

Properties and Items can both be used as parameters to Tasks.

## [Common (Built-in) Tasks](https://learn.microsoft.com/en-us/visualstudio/msbuild/msbuild-task-reference?view=vs-2022)
Several tasks, like MakeDir, are built in.
```xml
<Target Name="MakeBuildDirectory">
    <MakeDir Directories="$(BuildDir)" />
</Target>
```
# [Targets](https://learn.microsoft.com/en-us/visualstudio/msbuild/msbuild-targets?view=vs-2022)
Targets group tasks together in a sequence and expose sections of the project file as entry points into the build process.

# [Logging for MSBuild](https://learn.microsoft.com/en-us/visualstudio/msbuild/logging-in-msbuild?view=vs-2022)
