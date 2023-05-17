---
title: "notes > asp.net > web apps > blazor > blazor wasm > dependency injection"
date: 2023-04-18T00:00:00-06:00
draft: false
---

# Default Services
Among others:
| Service | Lifetime | Description |
|---------|----------|-------------|
`HttpClient` | Scoped | 
`IJSRuntime` | Singleton | An instance of a JavaScript runtime where JS calls are dispatched
`NavigationManager` | Singleton | Helpers for working with URI and navigation state

# Adding & Using Services
Note:  Blazor WASM apps do not have Scoped DI services.  If registered as Scoped, they will behave like Singleton.  This results in services having a longer lifetime than typical ASP.NET Core apps.

`Program.cs`
```cs
var builder = WebAssemblyHostBuilder.CreateDefault(args);
...
builder.Services.AddSingleton<WeatherService>();
builder.Services.AddSingleton<ISomeService, SomeService>();
...

var host = builder.Build();

// After the host is built, but before it's run, services are available from the root DI scope:
var weatherService = host.Services.GetRequiredService<WeatherService>();

// The host can also access configuration:
await weatherService.InitializeWeatherAsync(host.Configuration["WeatherServiceUri"]);

await host.RunAsync();
```

# Adding & Using Services — Hosted Blazor WASM
If common services are required between the Server and Client projects in a hosted Blazor WASM solution, place common service registrations in the Client project and call the method to register the services in both:
```cs
// Factor common service registrations into a separate method:
public static void ConfigureCommonServices(IServiceCollection services)
{
    services.Add...;
}
```
In Client's `Program.cs`, register the common services:
```cs
var builder = WebAssemblyHostBuilder.CreateDefault(args);
...
ConfigureCommonServices(builder.Services);
```
In Server's `Program.cs`, do the same, calling the Client's `ConfigureCommonServices` method:
```cs
var builder = WebApplication.CreateBuilder(args);
...
Client.Program.ConfigureCommonServices(builder.Services);
```

# [Detecting Transient Disposables in Blazor WASM Apps](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/dependency-injection?view=aspnetcore-7.0#detect-transient-disposables-in-blazor-webassembly-apps)
