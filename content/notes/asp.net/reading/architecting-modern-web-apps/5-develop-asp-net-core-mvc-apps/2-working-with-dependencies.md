---
title: 2 working with dependencies
date: 2023-04-14T00:00:00-06:00
draft: false
weight: 1
---

When evaluating how your app works with its dependencies, remember::

# The static cling code smell ([Static Cling | DevIQ](https://deviq.com/antipatterns/static-cling))
When classes make calls to static methods or access static properties which have side effects or dependencies on infrastructure, static cling occurs.
- Example: A method that calls a static method that writes to a database.  The caller is now tightly coupled to the database because anything that breaks the database call will break that method.
- Static calls that do not have any dependence on infrastructure (like calls that are completely stateless) are fine.

# The aphorism "new is glue" ([New is Glue | Blog (ardalis.com)](https://ardalis.com/new-is-glue/))
- Each time a class is instantiated, consider whether it makes sense to hard-code that specific instance in that location, or if it would be better to request that instance as a dependency.
- Just as with static method calls, new instances of types that have no external dependencies typically do not tightly couple code.
	
# Declaring Depedencies
In ASP.NET Core, methods and classes should declare their dependencies, requesting them as arguments.  The Startup class is an example of this.
Note: In ASP.NET 6+, the use of the Startup class is optional.  Apps can be fully configured in Program.cs.

## Configuring services in `Startup.cs`
The Startup class may have (but does not require) a constructor.  If it has one, you can request dependencies through it.
When the web host you have configured starts, it calls the `Startup` class:
```cs
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
            .SetBasePath(env.ContentRootPath)
            .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
            .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

You can also request dependencies in the Configure method:
```cs
public void Configure(IApplicationBuilder app, IHostingEnvironment env, ILoggerFactory loggerFactory)
{

}
```
The `ConfigureServices` takes a single `IServiceCollection` parameter.  It doesn't support DI because its responsible for adding objects to the DI container and it has access to the currently configured services via the `IServiceCollection`.
