---
title: services and dependency injection
date: 2023-01-08T00:00:00-06:00
draft: false
weight: 1
---

# Dependency Injection [[Documentation](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection?view=aspnetcore-7.0)]  

See notes on [Dependency Injection in .NET](../../../_net/dependency-injection/overview).

Makes configured services available throughout an app. ASP.NET Core templates automatically register over 250 services including:
- `IApplicationBuilderFactory`
- `IServiceProvider` as a built-in service container
- `ILogger<T>` (so a logger services does not need to be registered separately)
- `ILoggerFactory`
- `IHostApplicationLifetime`
- `IHostLifetime`
- `IHostEnvironment` or `IWebHostEnvironment`
- `IServer`
- `IOptions<T>`
- `DiagnosticSource`
- `DiagnosticListener`

Services are added to the DI container with `WebApplicationBuilder.Services` in `Program.cs`.
When `WebApplicationBuilder` is instantiated, many framework-provided services are added.
```cs
WebApplicationBuilder builder = WebApplication.CreateBuilder(args);

// Add services to the DI (services) container.
builder.Services.AddRazorPages();
builder.Services.AddControllersWithViews();

WebApplication app = builder.Build();
```

## Dependency Injection Chaining
This is common.  
Each requested dependency in turn requests its own dependencies.  
The DI container resolves the dependencies in a graph and returns the fully resolved service.  This is an object graph.  

# Registering Groups of Services
In ASP.NET, this is done with an `AddGroup_Name` extension method:
```cs
builder.Services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(connectionString));
```

# Service Lifetimes
ASP.NET Core uses the standard [.NET service lifetimes](../../../_net/dependency-injection/overview#service-lifetimes).

To inject scoped services, either:
- Inject the service into middleware's Invoke or InvokeAsync method.
    - <r>Do not use constructor injection</r> (this throws a runtime exception because it forces scoped services to behave like a singleton).
- Use [Factory-based middleware](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/middleware/extensibility?view=aspnetcore-7.0).

# Service Registration Methods
ASP.NET Core uses standard [.NET service registration methods](../../../_net/dependency-injection/overview#service-registration-methods).

Notes:
- If a service is registered with only an implementation type, you have registered that service with the same implementation and service type.
    - Stated differently:  multiple implementations of a service cannot be registered using methods that don't take an explicit service type.
    - Stated differently:  multiple instances of the service can be registered, but they will all have the same implementation type.

To exemplify:
```cs
services.AddSingleton<IMyDependency, MyDependency>();
services.AddSingleton<IMyDependency, DifferentDependency>(); // Overrides the previous call when resolved as IMyDependency; add to the previous call when resolved as IEnumerable<MyDependency>

public class MyService
{
    public MyService(IMyDependency myDependency, 
       IEnumerable<IMyDependency> myDependencies)
    {
        Trace.Assert(myDependency is DifferentDependency);

        var dependencyArray = myDependencies.ToArray();
        Trace.Assert(dependencyArray[0] is MyDependency);
        Trace.Assert(dependencyArray[1] is DifferentDependency);
    }
}
```

# Entity Framework Contexts
By default, Entity Framework contexts are added to the service container using the scoped lifetime because web app database operations are normally scoped to the client request. To use a different lifetime, specify the lifetime by using an `AddDbContext` overload. Services of a given lifetime shouldn't use a database context with a lifetime that's shorter than the service's lifetime.

## Requesting Services
Use `HttpContext.RequestServices` which will expose the scoped service provider.
<o>Note:</o> Prefer requesting services via constructor parameters vs. this approach as the former results in classes that are either to test.

# Disposal of Services
<o><b>Note</b>: never dispose of services resolved from the DI container</o>. The container calls `Dispose` for the `IDisposable` services it creates.

Here, `Service1`, `Service2`, and `Service3` are created by the DI container:
```cs
builder.Services.AddScoped<Service1>();
builder.Services.AddSingleton<Service2>();

var myKey = builder.Configuration["MyKey"];
builder.Services.AddSingleton<IService3>(sp => new Service3(myKey));
```

Here, they are not:
```cs
builder.Services.AddSingleton(new Service1());
builder.Services.AddSingleton(new Service2());
```

In the second example, `Service1` and `Service2` must be disposed of manually.