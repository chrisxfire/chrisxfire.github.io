---
title: notes > code > asp.net > ef core > dbcontext
date: 2023-05-23T00:00:00-06:00
draft: false
weight: 1
---

# Lifetime
The lifetime of `DbContext` begins when the instance is created and ends when it is disposed.  It lasts for a *unit of work*.

> A unit of work keeps track of everything you do during a business transaction that can affect the database.  When you're done, it figures out everything that needs to be done to alter the database as a result of the work."  

<br />

# Threading and Concurrency
<r>DbContext is not thread-safe</r>.  This includes parallel execution of async queries and any explicit concurrent use from multiple threads.  <g>Always await async calls immediately.</g>

## Concurrent access detection
EF Core detects attempts to use a `DbContext` instance concurrently and throws an `InvalidOperationException`.  Undetected attempts result in undefined behavior, crashes, and data corruption.

# Error Handling
An `InvalidOperationException` thrown by EF Core puts the context into an unrecoverable state.  The context must be discarded at this point.

# Creating & Configuring a `DbContext`
## Create a subclass of `DbContext`:
`SomeDbContext.cs`
```cs
public class SomeDbContext : DbContext
{
    public SomeDbContext(DbContextOptions<SomeDbContext> options) : base(options) 
    {
    }
}
```

## Register the `DbContext` in DI
Each DbContext instance must be configured to use exactly one database provider:
`Program.cs`
```cs
using Microsoft.EntityFrameworkCore;

builder.Services.AddDbContext<EmployeeManagerDbContext>(
    opt => 
        opt.UseSqlServer(builder.Configuration.GetConnectionString("EmployeeManagerDb")));
```

Database-provider specific configuration is performed in a provider-specific options builder:
```cs
builder.Services.AddDbContext<EmployeeManagerDbContext>(
    opt => 
        opt.UseSqlServer(
            builder.Configuration.GetConnectionString("EmployeeManagerDb"),
            providerOptions => { providerOptions.EnableRetryOnFailure() } ));
```
# Other DbContext Configuration Notes
## `DbContextOptions<T>` vs `DbContextOptions`
- `DbContext` subclasses that accept a `DbContextOptions` must use `DbContextOptions<T>` to ensure the correct options for that `DbContext` subtype are resolved from DI.
- If the DbContext subtype itself is intended to be inherited, use the `DbContextOptions`.

## DbContextOptionsBuilder methods
`DbContextOptionsBuilder` has other common methods for configuring the `DbContext`:
| Method | Description |
|--------|-------------|
UseQueryTrackingBehavior | Set the default tracking behavior for queries
LogTo | Provide a way to get EF Core logs
UseLoggerFactory | Registers a Microsoft.Extensions.Logging factory
EnableSensitiveDataLogging | Includes application data in exceptions and logging
EnableDetailedErrors | More detailed query errors (at the expense of performance)
ConfigureWarnings | Ignore or throw for warnings and other events
AddInterceptors | Register EF Core interceptors 
UseLazyLoadingProxies | Use dynamic proxies for lazy loading
UseChangeTrackingProxies | use dynamic proxies for change tracking

# Using `DbContext`
Inject the `DbContext` into the desired code via dependency injection:
```cs
public class SomeController
{
    private readonly SomeDbContext _context;

    public SomeController(SomeDbContext context) 
    {
        _context = context;
    }
}
```

