---
title: dotnet scaffold
date: 2024-12-05T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/dotnet/dotnet-cli/dotnet-scaffold
---

# Overview
`dotnet scaffold` is an interactive command line tool to scaffold ASP.NET Core projects.

- Reference: https://devblogs.microsoft.com/dotnet/introducing-dotnet-scaffold/

# Installation
`dotnet tool install --global Microsoft.dotnet-scaffold`

# Usage Example - General
`dotnet scaffold` follows a general pattern for all project types:

1. `dotnet scaffold` to start the interactive tool
2. Select a *scaffolding category* (project type) (like **Razor Pages**)
3. Select a *scaffolder* (like **Razor Page - Empty**)
4. Select the .NET project file (like **MyWebApp.csproj**)

The command scaffolds the project.

# Usage Example - Entity Framework Scaffolders
To scaffold EF, you first need a model class. Then, invoke `dotnet scaffold`:
1. Select scaffolding category **Razor Pages**
2. Select scaffolder **Razor Pages with Entity Framework (CRUD)** 
3. Select the .NET project file
4. Select the model class file
5. Enter the name of the database context (suffix it with `DbContext`)
6. Select the database provider (like **sqlite-efcore**)
7. Select the operations to scaffold (like **CRUD** or **Create**)

At this stage:
- the project file is updated with package references for Entity Framework
- `Program.cs` is updated to initialize the database connection
- `appsettings.json` is updated with connection information
- `*DbContext.cs` has been created and added to the project root
- Razor Pages for CRUD operations has been added to the `Pages` folder

8. Migrate the database: `dotnet ef migrations add initialMigration`
9. Update the database: `dotnet ef database update`