---
title: notes > code > cli > dotnet > containerization
date: 2023-03-10T13:32:54-0700
draft: false
---
# Configure Container Image
Most configuration is handled through MSBuild properties.
Exception: RUN commands require a Dockerfile.

## ContainerBaseImage
The image used as the basis for the image being created.
```xml
<PropertyGroup>
<ContainerBaseImage>mcr.microsoft.com/dotnet/runtime:6.0</ContainerBaseImage>
</PropertyGroup>
```

Defaults:
- If project is self-contained, the mcr.microsoft.com/dotnet/runtime-deps image is used.
- If project is an ASP.NET Core project, the mcr.microsoft.com/dotnet/aspnet image is used.
- Otherwise the mcr.microsoft.com/dotnet/runtime image is used.

## ContainerRuntimeIdentifier
The OS and architecture used by the container of the ContainerBaseImage supports more than one platform.
```xml
<PropertyGroup>
<ContainerRuntimeIdentifier>linux-amd64</ContainerRuntimeIdentifier>
</PropertyGroup>
```

Default: Set to value of the RuntimeIdentifier (-r option of dotnet publish command)

## ContainerRegistry
The destination registry.
```xml
<PropertyGroup>
<ContainerRegistry>registry.mycorp.com:1234</ContainerRegistry>
</PropertyGroup>
```

Default: local Docker daemon

## ContainerImageName
The name of the image.
```xml
<PropertyGroup>
<ContainerImageName>my-app</ContainerImageName>
</PropertyGroup>
```

Default: AssemblyName of project is used.

## ContainerImageTags
Tags generated for the image.
```xml
<PropertyGroup>
<ContainerImageTag>1.2.3-alpha2;another-tag</ContainerImageTag>
</PropertyGroup>
```

Default: Version of the project is used as tag value.

## ContainerWorkingDirectory
The working directory of the container.
```xml
<PropertyGroup>
<ContainerWorkingDirectory>/bin</ContainerWorkingDirectory>
</PropertyGroup>
```

Default: /app

## ContainerPort
TCP or UDP ports that are added to the list of known ports for the container.
```xml
<ItemGroup>
<ContainerPort Include="80" Type="tcp" />
</ItemGroup>
```

## ContainerLabel
A metadata label for the container.
```xml
<ItemGroup>
<ContainerLabel Include="org.contoso.businessunit" Value="contoso-university" />
</ItemGroup>
```

## ContainerEnvironmentVariable
Environment variables for the container.
```xml
<ItemGroup>
<ContainerEnvironmentVariable Include="LOGGER_VERBOSITY" Value="Trace" />
</ItemGroup>
```

## ContainerEntrypoint
The executable that is called when the container is started.
<ItemGroup Label="Entrypoint Assignment">
<!-- This is how you would start the dotnet ef tool in your container -->
<ContainerEntrypoint Include="dotnet" />
<ContainerEntrypoint Include="ef" />

<!-- This shorthand syntax means the same thing.
Note the semicolon separating the tokens. -->
<ContainerEntrypoint Include="dotnet;ef" />
</ItemGroup>
```

Default:
- For builds that create an app host, the app host is used as the Entrypoint.
- For builds that don't create an executable, dotnet path/to/app.dll is used.

## ContainerEntrypointArgs
Arguments passed to the ContainerEntrypoint.
```xml
<ItemGroup>
<!-- Assuming the ContainerEntrypoint defined above,
this would be the way to update the database by
default, but let the user run a different EF command. -->
<ContainerEntrypointArgs Include="database" />
<ContainerEntrypointArgs Include="update" />

<!-- This is the shorthand syntax for the same idea -->
<ContainerEntrypointArgs Include="database;update" />
</ItemGroup>
```

Default: None

# Process to Containerize an App
1.  Clean, Restore, Publish
```powershell
dotnet clean
dotnet restore
dotnet publish -c Release
```

2.  Create Dockerfile
Create the Dockerfile as file Dockerfile in the directory containing the csproj file:
```powershell
FROM mcr.microsoft.com/dotnet/runtime:7.0-bullseye-slim
WORKDIR /blsrpt
COPY bin/Release/net7.0/publish .
RUN apt-get update
RUN apt-get install -y libfreetype6
RUN apt-get install -y libfontconfig1
RUN apt-get install -y fontconfig
ENTRYPOINT ["dotnet", "blsrpt.dll"]
```

3.  Build image
```powershell
docker build -t *registry*/*image-name*:*tag* .
```

# [Publish App as Container Image](https://learn.microsoft.com/en-us/dotnet/core/docker/publish-as-container)
Requires docker.
```powershell
# For non-web apps:
dotnet publish --os linux --arch x64 /t:PublishContainer -c Release

# For web apps:
dotnet publish --os linux --arch x64 -p:PublishProfile=DefaultContainer
```
