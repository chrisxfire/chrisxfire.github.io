---
title: overview
date: 2023-01-13T00:00:00-06:00
draft: false
weight: -1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/logging/?view=aspnetcore-7.0

ASP.NET Core supports logging with built-in and third-party logging providers:  Console, Debug, Event Tracing, Windows Event Log, TraceSource, Azure App Service, Azure Application Insights.

- [Notes on Logging in .NET](../../../../_net/fundamentals/logging/overview) apply to these notes as well.
- Documentation:
    - [HTTP Logging in .NET Core and ASP.NET Core | Microsoft Learn](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/http-logging/?view=aspnetcore-7.0)
    - [W3CLogger in .NET Core and ASP.NET Core | Microsoft Learn](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/w3c-logger/?view=aspnetcore-7.0)

# Default Logging Providers
The default ASP.NET Core web app templates call `WebApplication.CreateBuilder` which adds the `Console`, `Debug`, `EventSource` and `EventLog` (Windows) logging providers.

Logs created with the default providers are displayed in:
- Visual Studio's Debug output window (when debugging)
- Visual Studio's ASP.NET Core Web Server window
- The console window if running with `dotnet run`.

To change the logging providers:  
`Program.cs`
```cs
var builder = WebApplication.CreateBuilder();
builder.Host.ConfigureLogging(logging =>
{
    logging.ClearProviders();
    logging.AddConsole();
});
```

<details>
<summary>
Default log levels and all default providers:
</summary>

```json
{
  "Logging": {
    "LogLevel": { // No provider, LogLevel applies to all the enabled providers.
      "Default": "Error",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Warning"
    },
    "Debug": { // Debug provider.
      "LogLevel": {
        "Default": "Information" // Overrides preceding LogLevel:Default setting.
      }
    },
    "Console": {
      "IncludeScopes": true,
      "LogLevel": {
        "Microsoft.AspNetCore.Mvc.Razor.Internal": "Warning",
        "Microsoft.AspNetCore.Mvc.Razor.Razor": "Debug",
        "Microsoft.AspNetCore.Mvc.Razor": "Error",
        "Default": "Information"
      }
    },
    "EventSource": {
      "LogLevel": {
        "Microsoft": "Information"
      }
    },
    "EventLog": {
      "LogLevel": {
        "Microsoft": "Information"
      }
    },
    "AzureAppServicesFile": {
      "IncludeScopes": true,
      "LogLevel": {
        "Default": "Warning"
      }
    },
    "AzureAppServicesBlob": {
      "IncludeScopes": true,
      "LogLevel": {
        "Microsoft": "Information"
      }
    },
    "ApplicationInsights": {
      "LogLevel": {
        "Default": "Information"
      }
    }
  }
}
```
</details>

# Creating Logs
To create logs, resolve an `ILogger<TCategoryName>` service from DI and call logging methods like `LogInformation`:
```cs
public class SomeClass {
    private readonly ILogger<SomeClass> _logger;
    
    public SomeMethod(ILogger<SomeClass> logger) {
        _logger = logger;
    }
    
    public async Task OnGetAsync() {
        _logger.LogInformation("SomeClass OnGetAsync.");
    }
}
```

# Configure Logging
Logging configuration is provided by the `Logging` section of `appsettings.ENVIRONMENT.json` files:

`appsettings.json`
```json
{
  "Logging": {
    "LogLevel": { // LogLevel applies to all the enabled providers.
      "Default": "Error", // Default logging, Error and higher.
      "Microsoft": "Warning" // All Microsoft* categories, Warning and higher.
    },
    "Debug": { // Debug provider.
      "LogLevel": {
        "Default": "Information", // Overrides preceding LogLevel:Default setting.
        "Microsoft.Hosting": "Trace" // Debug:Microsoft.Hosting category.
      }
    },
    "EventSource": { // EventSource provider.
      "LogLevel": {
        "Default": "Warning" // All categories of EventSource provider.
      }
    }
  }
}
```

The `Logging` property can contain `LogLevel` and logging provider properties.  See [Notes on Log Levels](../../../../_net/fundamentals/logging/overview#concepts).

# Creating Logs in Program.cs
The logger is available in `app` immediately after calling `builder.Builder()`:
`Program.cs`  
```cs {hl_lines=[5,7]}
var builder = WebApplication.CreateBuilder(args);

var app = builder.Build();

app.Logger.LogInformation("Adding Routes");
app.MapGet("/", () => "Hello World!");
app.Logger.LogInformation("Starting the app");
app.Run();
```

The loggers can also be modified before building:
```cs
var builder = WebApplication.CreateBuilder(args);

var logger = LoggerFactory.Create(config =>
{
    config.AddConsole();
}).CreateLogger("Program");

var app = builder.Build();

app.MapGet("/", () => "Hello World!");

app.MapGet("/Test", async context =>
{
    logger.LogInformation("Testing logging in Program.cs");
    await context.Response.WriteAsync("Testing");
});

app.Run();
```

# ASP.NET Core and EF Core Logging Categories
| Category                            | Notes                                                                                                             |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Microsoft.AspNetCore                | General ASP.NET Core diagnostics.                                                                                 |
| Microsoft.AspNetCore.DataProtection | Which keys were considered, found, and used.                                                                      |
| Microsoft.AspNetCore.HostFiltering  | Hosts allowed.                                                                                                    |
| Microsoft.AspNetCore.Hosting        | How long HTTP requests took to complete and what time they started. Which hosting startup assemblies were loaded. |
| Microsoft.AspNetCore.Mvc            | MVC and Razor diagnostics. Model binding, filter execution, view compilation, action selection.                   |
| Microsoft.AspNetCore.Routing        | Route matching information.                                                                                       |
| Microsoft.AspNetCore.Server         | Connection start, stop, and keep alive responses. HTTPS certificate information.                                  |
| Microsoft.AspNetCore.StaticFiles    | Files served.                                                                                                     |
| Microsoft.EntityFrameworkCore       | General Entity Framework Core diagnostics. Database activity and configuration, change detection, migrations.     |

# Filtering
See [these notes](../../../../_net/fundamentals/logging/overview#filters).

# Log Categories
See [these notes](../../../../_net/fundamentals/logging/overview#categories).

# Log Event IDs
See [these notes](../../../../_net/fundamentals/logging/overview#event-ids).

# Log Message Templates
See [these notes](../../../../_net/fundamentals/logging/overview#message-templates).

# Exceptions
See [these notes](../../../../_net/fundamentals/logging/overview#exceptions).

# Scopes
See [these notes](../../../../_net/fundamentals/logging/overview#scopes).

## ActivityTrackingOptions
Logging providers implicitly create a scope object with `SpanId`, `TraceId`, `ParentId`, `Baggage` and `Tags`.  This is configured via `ActivityTrackingOptions`:
```cs
var loggerFactory = LoggerFactory.Create(logging =>
  {
      logging.Configure(options =>
      {
          options.ActivityTrackingOptions = ActivityTrackingOptions.SpanId
                                              | ActivityTrackingOptions.TraceId
                                              | ActivityTrackingOptions.ParentId
                                              | ActivityTrackingOptions.Baggage
                                              | ActivityTrackingOptions.Tags;
      }).AddSimpleConsole(options =>
      {
          options.IncludeScopes = true;
      });
  });
```

More information: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/logging/?view=aspnetcore-7.0#automatically-log-scope-with-spanid-traceid-parentid-baggage-and-tags
