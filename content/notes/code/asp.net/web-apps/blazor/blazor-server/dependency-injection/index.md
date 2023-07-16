---
title: notes > code > asp.net > web apps > blazor > blazor server > dependency injection
date: 2023-04-18T00:00:00-06:00
draft: false
weight: 1
---

# Default Services
Among others:
| Service | Lifetime | Description |
|---------|----------|-------------|
`IJSRuntime` | Scoped | An instance of a JavaScript runtime where JS calls are dispatched
`NavigationManager` | Scoped | Helpers for working with URI and navigation state

# Adding & Using Services
Note:  In ASP.NET Core apps, scoped services are typically scoped to the current request.  In Blazor Server apps, the request scope lasts for the duration of the client connection.

`Program.cs`
```cs
var builder = WebApplication.CreateBuilder(args);

// builder has an IServiceCollection which is a list of service descriptor objects
builder.Services.AddRazorPages();
builder.Services.AddServerSideBlazor();
builder.Services.AddSingleton<WeatherForecastService>();
builder.Services.AddSingleton<ISomeService, SomeService>();
```

# [Detect Transient Disposables in Blazor Server Apps](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/dependency-injection?view=aspnetcore-7.0#detect-transient-disposables-in-blazor-server-apps)

# How a Component Can Access Services from a Different DI Scope
If a component invokes an async method that executes code in a different DI scope, they do not have access to the DI container's services (like `IJSRuntime`).  An example is `HttpClient` instances instantiated from `IHttpClientFactory`, which have their own DI scope.

To resolve, create a class `BlazorServiceAccessor` that defines an AsyncLocal which stores the `IServiceProvider` for the current async context.  An instance of this class can be acquired from within a different DI scope.
```cs
internal sealed class BlazorServiceAccessor
{
    private static readonly AsyncLocal<BlazorServiceHolder> s_currentServiceHolder = new();

    public IServiceProvider? Services
    {
        get => s_currentServiceHolder.Value?.Services;
        set
        {
            if (s_currentServiceHolder.Value is { } holder)
                holder.Services = null; // Clear the current IServiceProvider trapped in the AsyncLocal.

            if (value is not null)
                // Use object indirection to hold the IServiceProvider in an AsyncLocal
                // so it can be cleared in all ExecutionContexts when it's cleared.
                s_currentServiceHolder.Value = new() { Services = value };
        }
    }

    private sealed class BlazorServiceHolder
    {
        public IServiceProvider? Services { get; set; }
    }
}
```
