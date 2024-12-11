---
title: libman
date: 2023-04-22T00:00:00-07:00
draft: false
weight: 1
---

# Overview
Library Manager (LibMan) is included in Visual Studio. LibMan allows you to add external libraries such as Bootstrap.  


# How
## Via Visual Studio
Right-click project > **Add** > **Client-Side Library…**

## Via [LibMan CLI](https://learn.microsoft.com/en-us/aspnet/core/client-side/libman/libman-cli?view=aspnetcore-7.0)
1. Install the LibMan CLI as a dotnet tool:
   ```powershell
   dotnet tool install -g Microsoft.Web.LibraryManager.Cli
   ```
2. Initialize LibMan in the project:
   ```powershell
   libman init
   ```
   This creates a `libman.json` file if one does not already exist.
3. Add libraries:
   ```powershell
   libman install <library>
    --destination <path>
    --files <file-to-install> # if not specified, install all files in package
    --provider <cdnjs|filesystem|jsdeliver|unkpg>
   ```

# Bootstrap
Add to `/wwwroot/lib/bootstrap`
