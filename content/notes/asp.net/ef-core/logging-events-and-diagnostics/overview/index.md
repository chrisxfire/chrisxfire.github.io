---
title: "notes > asp.net > ef core > logging events and diagnostics > overview"
date: 2023-06-14T00:00:00-06:00
draft: false
---

# Logging Mechanisms Quick Reference
| Mechanism                    | Async | Scope       | Registered                  | Intended Use               |
| ---------------------------- | ----- | ----------- | --------------------------- | -------------------------- |
| Simple logging               | No    | Per context | Context configuration       | Development-time logging   |
| Microsoft.Extensions.Logging | No    | Per context | DI or context configuration | Production logging         |
| Events                       | No    | Per context | Any time                    | Reaching to EF events      |
| Interceptors                 | Yes   | Per context | Context configuration       | Manipulating EF operations |
| Diagnostics listeners        | No    | Process     | Globally                    | Application diagnostics    |

# Simple logging
Use `LogTo` when configuring a `DbContext` instance:
```cs
protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder) =>
    optionsBuilder.LogTo(Console.WriteLine);
```

# Microsoft.Extensions.Logging
Use like any ASP.NET Core application.

# Events
Act as callbacks when an event occurs in EF Core.  These are easier to use than interceptors, but they are synchronous only and cannot perform non-blocking async I/O.  

Events are registered per `DbContext` instance.  Use a diagnostic listener to get the same information but for all `DbContext` instances in the process.

# Interceptors
Enable interception, modification, and/or suppression of EF Core operations, including low-level operations like executing a SQL command.  If the only requirement is logging, interceptors are not the best choice.

# Diagnostic listeners
Allow listening for EF Core events that occur in the current .NET process.