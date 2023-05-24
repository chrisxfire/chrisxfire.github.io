---
title: "notes > asp.net > efcore > overview"
date: 2023-05-22T00:00:00-06:00
draft: false
---
  
*From Microsoft Learn / Entity Framework / Entity Framework Core*

# Overview
Entity Framework (EF) Core is a data access technology that can serve as an object-relational mapper (OR/M).  It supports various *database providers*.

Data access is performed using a *model* that includes *entity* classes and a context object that represents a session with a database.

## Model development approaches
1. Generate a model from an existing database  
2. Hand code a model to match a database  
3. Use EF Migrations to create a database from a model  

# Installing
## Install EF Core w/SQL Server Database Provider
```posh
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

## Install .NET Core CLI tools
```posh
dotnet tool install --global dotnet-ef
dotnet add package Microsoft.EntityFrameworkCore.Design
```

## Install Package Manager Console tools
```posh
dotnet add package Microsoft.EntityFrameworkCore.Tools
```

# Performing Migrations
## via .NET Core CLI
```posh
dotnet ef migrations add InitialCreate
dotnet ef database update
```

## via Package Manager Console
```posh
Add-Migration InitialCreate
Update-Database
```

This creates:
- `Migrations/EmployeeManagerDbContextSnapshot` — a snapshot of the current database state
- `Migrations/###_InitialCreate.cs` — contains:
    - `Up` method — creates the database tables
    - `Down` method — drops the tables

### Run the migration
```powershell
PM> update-database
```

### Confirm the database exists  
Visual Studio > **View** > **SQL Server Object Explorer**

# Using the `DbContext` in a Component
`Pages/EmployeeOverview.razor`
```html
@page "/employees/list"
@using Microsoft.EntityFrameworkCore; @* ToArrayAsync *@
@using WiredBrainCoffee.EmployeeManager.Data.Models;
@using WiredBrainCoffee.EmployeeManager.Data;
<!-- Inject the DbContext into this Component: --> 
@inject EmployeeManagerDbContext Context

<PageTitle>Employees</PageTitle>
<h1>Employees</h1>

TODO: List the employees here.
```
```cs
@code
{
    private Employee[]? Employees { get; set; }

    protected override async Task OnInitializedAsync()
    {
        // The DbContext has a DbSet<Employee> that we use to set the Employees property.
        // The Include method specifies related entities to include in the query.
        // In this case, since Employee has a Department property, that it a related entity we need to include.
        Employees = await Context.Employees.Include(emp => emp.Department).ToArrayAsync();
    }
}
```

# Using DbContextFactory
By injecting a `DbContext` into a Component, the lifetime of the `DbContext` is now tightly coupled to the Component. In Blazor Server, since the client (browser) is connected to the server via a SignalR connection, the Component is not re-created for each request; the Component lives as long as the client is using it.  The `DbContext` is designed for a short lifespan.  

To avoid this problem, inject an `IDbContextFactory` into the Component instead. It can be used to inject a short-lived context.
`IDbContextFactory` registers both an `IDbContextFactory` (short-lived) and a `DbContext` (long-lived) as services:
`Program.cs`
```cs
builder.Services.AddDbContextFactory<EmployeeManagerDbContext>(
    opt => opt.UseSqlServer(builder.Configuration.GetConnectionString("EmployeeManagerDb")));
```

`Pages/EmployeeOverview.razor`
```html
@page "/employees/list"
@using Microsoft.EntityFrameworkCore; @* ToArrayAsync *@
@using WiredBrainCoffee.EmployeeManager.Data.Models;
@using WiredBrainCoffee.EmployeeManager.Data;
<!-- Inject the DbContext into this Component: --> 
@inject IDbContextFactory<EmployeeManagerDbContext> ContextFactory

<PageTitle>Employees</PageTitle>
<h1>Employees</h1>
```
```cs
@code
{
    private Employee[]? Employees { get; set; }

    protected override async Task OnInitializedAsync()
    {
        using var context = ContextFactory.CreateDbContext();

        Employees = await context.Employees.Include(emp => emp.Department).ToArrayAsync();
    }
}
```
# Database Providers
| Database System | Package |
| ----------------| --------|
| SQL Server & SQL Azure | `Microsoft.EntityFrameworkCore.SqlServer ` |
| SQLite                 | `Microsoft.EntityFrameworkCore.Sqlite`     |
| Azure Cosmos DB        | `Microsoft.EntityFrameworkCore.Cosmos`     |
| PostgreSQL             | `Microsoft.EntityFrameworkCore.PostgreSQL` |
| MySQL                  | `Microsoft.EntityFrameworkCore.MySql`      |
| In-memory database     | `Microsoft.EntityFrameworkCore.InMemory`   |