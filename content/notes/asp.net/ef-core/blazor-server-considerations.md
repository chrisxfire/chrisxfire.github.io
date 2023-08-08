---
title: blazor server considerations
date: 2023-05-24T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Blazor Server's stateful app framework requires a special approach to use EF Core.  For example, in Blazor Server apps, scoped services registrations can be problematic because the instance is shared across components within a user's circuit.  `DbContext` is not thread safe and not designed for concurrent use.  

There are two patterns:
1. Context-per-operation
2. Context-per-component

# Context-per-operation
Use this approach by default:
```cs
using var context = new SomeContext();

return away context.SomeEntities.ToListAsync();
```

In this pattern, use a flag to prevent multiple concurrent operations:
```cs
if (Loading)
    return

try
{
    Loading = true;

    // ...
}
finally
{
    Loading = false;
}
```

Considerations:
- This loading logic should be used to disable UI controls so users do not inadvertently select buttons or update fields while data is being fetched.
- If there is any possibility of multiple threads accessing the same code block, inject a factory and make a new instance per operation.

# Context-per-component
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
        // The DbContext has a DbSet<Employee> that we use to set the Employees  property.
        // The Include method specifies related entities to include in the query.  
        // In this case, since Employee has a Department property, that it a related entity we need to include.
        Employees = await Context.Employees.Include(emp => emp.Department).ToArrayAsync();
    }
}
```

## Using DbContextFactory
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
