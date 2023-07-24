---
title: notes > asp.net > web apps > blazor > fundamentals > logging
date: 2023-04-18T00:00:00-06:00
draft: false
weight: 1
---

# Overview
At default log levels, and with no additional providers:
- Blazor Server logs to the server-side .NET console in Development environment at `LogLevel.Information` or higher.
- Blazor WASM logs to the client-side browser developer tools console at `LogLevel.Information` or higher.

Documentation: https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/logging?view=aspnetcore-7.0

# Logging in Components
## Injecting an ILogger  
`Pages/Counter1.razor`
```html
@page "/counter-1"
@inject ILogger<Counter> logger

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>
```
```cs
@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        logger.LogWarning("Someone has clicked me!");

        currentCount++;
    }
}
```

## Logging with ILoggerFactory
`Pages/Counter2.razor`
```html
@page "/counter-2"
@inject ILoggerFactory LoggerFactory

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>
```
```cs
@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        var logger = LoggerFactory.CreateLogger<Counter>();
        logger.LogWarning("Someone has clicked me!");

        currentCount++;
    }
}
```

# Logging in Blazor Server
There are no special logging considerations for Blazor Server.  See the notes for [logging in ASP.NET Core](../../../fundamentals/logging/overview.md).

# Logging in Blazor WASM
Configure logging in Blazor WASM apps with the `WebAssemblyHostBuilder.Logging` property via extension methods on `builder.Logging`.

Blazor WASM supports the following .NET logging features:

## Log in Program.cs
This is supported after the `WebAssemblyHostBuilder` is built:
```cs
var host = builder.Build();

var logger = host.Services.GetRequiredService<ILoggerFactory>()
    .CreateLogger<Program>();

logger.LogInformation("Logged after the app is built in Program.cs.");

await host.RunAsync();
```

## Log Categories
`Pages/Counter.razor`
```cs
var logger = LoggerFactory.CreateLogger("CustomCategory");
logger.LogWarning("Someone has clicked me!");
```

## Log Event ID
`LogEvent.cs`
```cs
public class LogEvent
{
    public const int Event1 = 1000;
    public const int Event2 = 1001;
}
```

`Pages/Counter.razor`
```cs
logger.LogInformation(LogEvent.Event1, "Someone has clicked me!");
logger.LogWarning(LogEvent.Event2, "Someone has clicked me!");
```

## Log Message Templates
`Pages/Counter.razor`
```cs
logger.LogInformation("Someone clicked me at {CurrentDT}!", DateTime.UtcNow);
```

## Log Exception Parameters
`Pages/Counter.razor`
```cs
currentCount++;

try
{
    if (currentCount == 3)
    {
        currentCount = 4;
        throw new OperationCanceledException("Skip 3");
    }
}
catch (Exception ex)
{
    logger.LogWarning(ex, "Exception (currentCount: {Count})!", currentCount);
}
```

## Filter Functions
`Program.cs`
```cs
builder.Logging.AddFilter((provider, category, logLevel) =>
    category.Equals("CustomCategory2") && logLevel == LogLevel.Information);
```

`Pages/Counter.razor`
```cs
var logger1 = LoggerFactory.CreateLogger("CustomCategory1");
logger1.LogInformation("Someone has clicked me!");

var logger2 = LoggerFactory.CreateLogger("CustomCategory1");
logger2.LogWarning("Someone has clicked me!");

var logger3 = LoggerFactory.CreateLogger("CustomCategory2");
logger3.LogInformation("Someone has clicked me!");

var logger4 = LoggerFactory.CreateLogger("CustomCategory2");
logger4.LogWarning("Someone has clicked me!");
```

### Example
To disable log messages specific to `Microsoft.AspNetCore.Components.RenderTree`, either:
```cs
builder.Logging.AddFilter("Microsoft.AspNetCore.Components.RenderTree.*", LogLevel.None);
```

...or...
```cs
builder.Services.PostConfigure<LoggerFilterOptions>(options =>
    options.Rules.Add(
        new LoggerFilterRule(null, 
                             "Microsoft.AspNetCore.Components.RenderTree.*", 
                             LogLevel.None, 
                             null)
    ));
```

## Custom Logging Provider
See https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/logging?view=aspnetcore-7.0#custom-logger-provider-blazor-webassembly

## Log Scopes
The Blazor WASM developer tools console <u>does not</u> support log scopes. A custom logger that supports log scopes would need to be implemented.

# Hosted Blazor WASM Logging
A hosted Blazor WebAssembly app that prerenders its content executes component initialization code twice. Logging takes place server-side on the first execution of initialization code and client-side on the second execution of initialization code. Depending on the goal of logging during initialization, check logs server-side, client-side, or both.

# SignalR Client Logging (Blazor Server)
In `Pages/_Host.cshtml`, pass in the `configureSignalR` object that calls `configureLogging` with the log level.  Pass either a string (`"trace"`, `"debug"`, `"information"`, `"warning"`, `"error"`, `critical` or `none`) or a corresponding integer `0` to `6`.

`Pages/_Host.cshtml`
```html
<script src="_framework/blazor.server.js" autostart="false"></script>
<script>
  Blazor.start({
    configureSignalR: function (builder) {
      builder.configureLogging("information");
    }
  });
</script>
```

# SignalR Client Logging (Blazor WASM)
Provide a `Logging:LogLevel:HubConnection` app setting in the default `appsettings.json` file and in the Development environment app settings file:  
`wwwroot/appsettings.json`  
```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning",
      "HubConnection": "Warning"
    }
  }
}
```

`wwwroot/appsettings.Development.json`
```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning",
      "HubConnection": "Trace"
    }
  }
}
```

Next, in a component, use a `WebAssemblyConsoleLogger`. This is a wrapper around browser-specific logging APIs:
```html
<!-- This LoggerProvider will be used to add a WebAssemblyConsoleLogger: -->
@inject ILoggerProvider LoggerProvider
@inject IConfiguration Config
@inject NavigationManager Navigation
```

Next, in that component's `OnInitializedAsync` method, add the logging provider in a `HubConnectionBuilder`:
```cs
protected override async Task OnInitializedAsync()
{
    hubConnection = new HubConnectionBuilder()
        .WithUrl(Navigation.ToAbsoluteUri("/chathub"))
        .ConfigureLogging(builder => 
        {
            builder.AddProvider(LoggerProvider);
            builder.SetMinimumLevel(
                Config.GetValue<LogLevel>("Logging:LogLevel:HubConnection"));
        })
        .Build();

    hubConnection.On<string, string>("ReceiveMessage", (user, message) => ...

    await hubConnection.StartAsync();
}
```

# Authentication Logging
Blazor authentication messages can be logged with either of these approaches:

In an appsettings file via logger configuration:
```json
"Logging": {
  "LogLevel": {
    "Microsoft.AspNetCore.Components.WebAssembly.Authentication": "Debug"
  }
}
```

...or...

In `Program.cs` via a log filter:
```cs
#if DEBUG
    builder.Logging.AddFilter(
        "Microsoft.AspNetCore.Components.WebAssembly.Authentication", 
        LogLevel.Debug);
#endif
```
