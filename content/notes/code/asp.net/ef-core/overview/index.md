---
title: notes > code > asp.net > ef core > overview
date: 2023-05-22T00:00:00-06:00
draft: false
---
  
*From Microsoft Learn / Entity Framework / Entity Framework Core*

# Overview
Entity Framework (EF) Core is a data access technology that can serve as an object-relational mapper (OR/M).  It supports various *database providers*.

Data access is performed using a *model* that includes *entity* classes and a *context* object that represents a session with a database.

An *entity* is a database.  
An *entity set* is a table in the database.

## Model development approaches
1. Generate a model from an existing database  
2. Hand code a model to match a database  
3. Use EF Migrations to create a database from a model  

# Installing
## Install EF Core w/SQL Server Database Provider
```powershell
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

## Install .NET Core CLI tools
```powershell
dotnet tool install --global dotnet-ef
dotnet add package Microsoft.EntityFrameworkCore.Design
```

## Install Package Manager Console tools
```powershell
dotnet add package Microsoft.EntityFrameworkCore.Tools
```

# Performing Migrations
## via .NET Core CLI
```powershell
dotnet-ef migrations add InitialCreate
dotnet-ef database update
```

## via Package Manager Console
```powershell
Add-Migration InitialCreate
Update-Database
```

This creates:
- `Migrations/EmployeeManagerDbContextSnapshot` — a snapshot of the current database state
- `Migrations/###_InitialCreate.cs` — contains:
    - `Up` method — creates the database tables
    - `Down` method — drops the tables

### Confirm the database exists  
Visual Studio > **View** > **SQL Server Object Explorer**

# Database Providers
| Database System | Package |
| ----------------| --------|
| SQL Server & SQL Azure | `Microsoft.EntityFrameworkCore.SqlServer ` |
| SQLite                 | `Microsoft.EntityFrameworkCore.Sqlite`     |
| Azure Cosmos DB        | `Microsoft.EntityFrameworkCore.Cosmos`     |
| PostgreSQL             | `Microsoft.EntityFrameworkCore.PostgreSQL` |
| MySQL                  | `Microsoft.EntityFrameworkCore.MySql`      |
| In-memory database     | `Microsoft.EntityFrameworkCore.InMemory`   |
