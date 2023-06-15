---
title: notes > .net > fundamentals > services > worker services
date: 2022-06-27T08:19:08-0600
draft: false
---

# Terminology
*Background Service* – the `BackgroundService` type.
*Hosted Service* – an implementation of `IHostedService`, or `IHostedService` itself.
*Worker Service* – the [Worker Service template](https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-new-sdk-templates#web-others) from dotnet new.

# [BackgroundService](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.hosting.backgroundservice)
An implementation of [IHostedService](https://docs.microsoft.com/en-us/dotnet/api/microsoft.extensions.hosting.ihostedservice).
Used for long-running, background processes.
Cross-platform. Can be used in place of a Windows Service.

# Worker Service
dotnet new worker produces:
`Program.cs`:
```cs
using *SomeNamespace*;

// Create the default IHostBuilder:
IHost host = Host.CreateDefaultBuilder(args).ConfigureServices(services =>
{
    // Add the Worker class as a hosted service:
    services.AddHostedService<Worker>();
})
// Build the IHost:
.Build();
// Run the app:
await host.RunAsync();
```
`Worker.cs`:
```cs
namespace *SomeNamespace*;

public class Worker : BackgroundService 
{ // BackgroundService implements `IHostedService`.
    private readonly ILogger<Worker> _logger;

    public Worker(ILogger<Worker> logger) => _logger = logger;
    protected override async Task ExecuteAsync(CancellationToken stoppingToken) 
    {
        // Loop once per second and log the datetime:
        while (!stoppingToken.IsCancellationRequested) 
        {
            _logger.LogInformation("Worker running at: {time}", DateTimeOffset.Now);
            await Task.Delay(1000, stoppingToken);
        }
    }
}
```
## No Server Garbage Collection
[Server GC](https://docs.microsoft.com/en-us/dotnet/standard/garbage-collection/workstation-server-gc#server-gc) is not enabled by default. To do so, add this to project file:
```xml
<PropertyGroup>
<ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```
[More info](https://docs.microsoft.com/en-us/dotnet/core/runtime-config/garbage-collector#workstation-vs-server).
