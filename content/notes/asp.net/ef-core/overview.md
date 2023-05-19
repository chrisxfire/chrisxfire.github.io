---
title: "notes > asp.net > efcore > overview"
date: 2023-05-16T00:00:00-06:00
draft: false
---

From Pluralsight/Building a Data-driving ASP.NET Core 6 Blazor Server Application

# Implement a Database with EF Core in an ASP.NET Core Blazor Web App
## Create Model classes
`Data/Models/Employee.cs`
```cs
public class Employee
{
    public int Id { get; set; } // Primary Key
    [Required] // even though it's nullable, this property is required
    [StringLength(50)]
    public string? FirstName { get; set; }
    [Required]
    [StringLength(50)]
    public string? LastName { get; set; }
    public bool IsDeveloper { get; set; }
    [Required] // an Employee MUST be in a Department
    public int? DepartmentId { get; set; } // Foreign Key
    public Department? Department { get; set; }
}
```

`Data/Models/Department.cs`
```cs
public class Department
{
    public int Id { get; set; }
    [Required]
    [StringLength(50)]
    public string? Name { get; set; }
    public List<Employee> Employees { get; set; } = new();
}
```
## Implement a DbContext
dotnet add package microsoft.entityframeworkcore.sqlserver

`Data/EmployeeManagerDbContext.cs`
```cs
public class EmployeeManagerDbContext : DbContext
{
    /*
    In previous versions of C#, Employees would throw a null warning here. To resolve this,  
    you would use the Set method of the DbContext base class to set Employees to a default value:  
    public DbSet<Employees> Employees => Set<Employee>();  
    */
    public DbSet<Employee> Employees { get; set; }
    public DbSet<Department> Departments { get; set; }

    public EmployeeManagerDbContext(DbContextOptions<EmployeeManagerDbContext> options) : base(options)
    {
    }
}
```

## Register the DbContext in DI
`Program.cs`
```cs
builder.Services.AddDbContext<EmployeeManagerDbContext>(
    opt => opt.UseSqlServer(builder.Configuration.GetConnectionString("EmployeeManagerDb")));
```

## Set the Connection String in `appsettings.json`
`appsettings.json`
```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
  "ConnectionStrings": {
    // localDb = SQL Server development database
    // MSSQLLocalDb = username
    "EmployeeManagerDb": "Data Source=(localDb)\\MSSQLLocalDb;Initial Catalog=EmployeeManagerDb"
  }
}
```

## Execute a Migration
### Add a migration
`dotnet add package microsoft.entityframeworkcore.tools`

```powershell
PM> add-migration InitialCreate
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
**View** > **SQL Server Object Explorer**

# Using the DbContext in a Component
`Pages/EmployeeOverview.razor`
```html
@page "/employees/list"
@using Microsoft.EntityFrameworkCore; @* ToArrayAsync *@
@using WiredBrainCoffee.EmployeeManager.Data.Models;
@using WiredBrainCoffee.EmployeeManager.Data;
@* Inject the DbContext into this Component: *@
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