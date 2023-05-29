---
title: "notes > dotnet > core > generic host"
date: 2022-06-26T19:15:58-0600
draft: false
---
# [Generic Host](https://docs.microsoft.com/en-us/dotnet/core/extensions/generic-host)
`Microsoft.Extensions.Hosting`

A host is an object that encapsulates an app's resources and lifetime functionality. This allows for control over the app's startup and graceful shutdown.
- Examples: Dependency Injection, Logging, Configuration, `IHostedService` implementations

Generic Host is represented by the `HostBuilder` type.

# Process
When a host starts, it calls `IHostedService.StartAsync` on each implementation of `IHostedService` registered in the service container's collection of hosted services. If the implementation is a worker service, it calls `BackgroundService.ExecuteAsync`.

# Execution Sequence
1.  StartAsync
2.  OnStarted
3.  OnStopping
4.  StopAsync
5.  OnStopped

# Creating
Hosts are usually built, configured, and run in `Program.Main`:

## Default Host
```cs
await Host.CreateDefaultBuilder(args) // Create the default `IHostBuilder`.
    .ConfigureServices((hostContext, services) =>
    
    {
        // This method allows you to add services to the `IServiceCollection` instance:
        services.AddHostedService<*SomeClass*>();
    })
    .RunConsoleAsync(); // Includes `UseConsoleLifetime().Build().RunAsync()`;
```
Pre-configuration includes:
- Content root path is set to CWD.
- Host configuration is loaded from:
  - (1) Environment variables prefixed with DOTNET_
  - (2) Command line arguments
- App configuration is loaded from:
  - (1) appsettings.json (or appsettings.{Environment}.json)
  - (2) Secret Manager (if running in the Development environment)
  - (3) Environment variables.
  - (4) Command line arguments.
- These logging providers are automatically added: `Console`, `Debug`, `EventSource`, `EventLog` (Windows only)
- These services are registered automatically: `IHostApplicationLifetime`, `IHostLifetime`, `IHostEnvironment`

## Non-Default Host
```cs
IHostBuilder builder =
    new HostBuilder().ConfigureServices((hostContext, services) =>
    
    {
        services.AddHostedService<IntegrationService>();
    });

await builder.RunConsoleAsync();
```
# IHostEnvironment
Inject this service into a class to get info about these settings:
- `IHostEnvironment.ApplicationName`
- `IHostEnvironment.ContentRootFileProvider`
- `IHostEnvironment.ContentRootPath`
- `IHostEnvironment.EnvironmentName`

# Host Configuration
Configures properties of the `IHostEnvironment` implementation.
Call `ConfigureHostConfiguration()` on `IHostBuilder` to configure:
```cs
IHost host = Host.CreateDefaultBuilder(args)
    .ConfigureHostConfiguration(configHost => 
    {
    configHost.SetBasePath(…);
    configHost.AddJsonFile("somefile.json", option: true);
    configHost.AddEnvironmentVariables(prefix: "PREFIX_");
    configHost.AddCommandLine(args);
})
.Build();
```

# App Configuration
Call `ConfigureAppConfiguration()` on `IHostBuilder`.
This can be called repeatedly; the last value set on a given key is used.

The host configuration is contained within `HostBuilderContext.Configuration` within the `ConfigureAppConfiguration` method.

See <https://docs.microsoft.com/en-us/dotnet/core/extensions/configuration>.

# Host Shutdown
Hosted services are stopped as follows:
- If the app exits normally with `Main()` completing and neither `Run()` nor `HostingAbstractionsHostExtensions.WaitForShutdown()` is called.
- The app crashes.
- The app is sent SIGKILL (Ctrl+Z)
- If `ConsoleLifetime` is used, it listens for these signals and attempts graceful shutdown:
  - SIGINT (Ctrl+C), SIGQUIT (Ctrl+Break), SIGTERM (sent by other apps).
- If the app calls `Environment.Exit()`.
  - Note: `Environment.Exit()` is NOT a graceful shutdown in the Hosting app model.

To gracefully shut down a host on demand, call `IHostApplicationLifetime.StopApplication()`.

# IHostApplicationLifetime
Inject this service into any class to handle post-startup and graceful shutdown tasks.

Properties:
- `ApplicationStarted`, `ApplicationStopping`, `ApplicationStopped`
- These properties are triggered on events.

Methods:
- `StopApplication()`

## Example
```cs
namespace SomeNamespace;

public class SomeService : IHostedService 
{
    private readonly ILogger _logger;

    public SomeService(ILogger<SomeClass> logger, IHostApplicationLifetime appLifetime, …) 
    {
        _logger = logger;
        appLifetime.ApplicationStarted.Register(OnStarted);
        appLifetime.ApplicationStopping.Register(OnStopping);
        appLifetime.ApplicationStopped.Register(OnStopped);
    }

    public Task StartAsync(CancellationToken cxlToken) 
    {
        _logger.LogInformation("Starting…");
    }

    public task StopAsync(CancellationToken cxlToken) 
    {
        _logger.LogInformation("Stopping…");
    }

    private void OnStarted() 
    {
        _logger.LogInformation("OnStarted called.");
    }

    private void OnStopping() 
    {
        _logger.LogInformation("OnStopping called.");
    }

    private void OnStopped() 
    {
        _logger.LogInformation("OnStopped called.");
    }
}
```
Above, in `Program.Main`, instead of `Worker`, `SomeService` could now be used.

Call the interface's `StopApplication()` method to shutdown on demand.

# IHostLifetime
Controls when the host starts and stops. The last implementation registered is used.

Methods:
- `StopAsync()`, `WaitForStartAsync()`