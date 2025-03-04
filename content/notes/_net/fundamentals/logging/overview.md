---
title: overview
date: 2022-06-22T00:00:00-06:00
draft: false
weight: -1
---

# Abstract [[Documentation](https://learn.microsoft.com/en-us/dotnet/core/extensions/logging?tabs=command-line)]  
.NET's logging API supports a variety of built-in and third-party logging providers.

# concepts
- Logging *providers* — an implementation of `ILogger<T>` that outputs logs 
- Logging *categories* — a string associated with each log message
- Logging *levels*:
    - `Trace` = 0 (<r>Warning</r>: may contain sensitive app data; do not enable in production)
    - `Debug` = 1 (<o>Caution</o>: may produce a high volume of logs)
    - `Information` = 2 (default if no level specified)
    - `Warning` = 3 (errors and conditions that do not cause the app to fail)
    - `Error` = 4 (errors and exceptions in the scope of the current operation (not app-wide) that cannot be handled)
    - `Critical` = 5 (failures that require immediate attention)
    - `None` = 6 (use this level to suppress log messages)

# Providers [[Documentation](https://learn.microsoft.com/en-us/dotnet/core/extensions/logging-providers)]  

Built-in providers include:
- `Debug` — uses `System.Diagnostics.Debug` via `Debug.WriteLine` method and only when a debugger is attached
	- `DebugLoggerProvider` creates `DebugLogger` instances which implement `ILogger.`
- `Console` — logs output to the console
- `EventSource` — a cross-platform event source; on Windows, Event Trace for Windows (ETW)
  - Note: `dotnet-trace` depends on `EventSource.`
- `EventLog` — the Windows Event Log; <o>does not inherit default non-provider settings</o>; defaults to `LogLevel.Warning`
- `AzureAppServicesFile` — writes logs to text files in an Azure App Service app's file system
- `AzureAppServicesBlob` — writes logs to text files in blob storage in an Azure Storage account
- `dotnet trace` tool — see [dotnet-trace diagnostic tool - .NET CLI | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/core/diagnostics/dotnet-trace) and [Debug high CPU usage - .NET Core | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/core/diagnostics/debug-highcpu?tabs=windows)

The default providers in the Worker app template are `Console`, `Debug`, `EventSource`, and `EventLog` (Windows only).

# registering logging services
In .NET 6+, logging services register a generic `ILogger<T>` instead of a non-generic `ILogger`.

Logging with Generic Host:
```cs
class Program {
	static Task Main(string[] args) {
		// Create the host:
		IHost host = Host.CreateDefaultBuilder(args)
			// By default, these logging providers are added by CreateDefaultBuilder: Console, Debug, EventSource, EventLog (Windows only)
			.ConfigureLogging(logging => {
				logging.ClearProviders(); // Clear the default logging providers.
				logging.SetMinimumLevel(LogLevel.Warning); // Set the minimum log level if not found in configuration.
				logging.AddConsole(); // Only add the Console logging provider back.
			.Build();
		
		// Get an ILogger instance from DI:
		var logger = host.Services.GetRequiredService<ILogger<Program>>();
		logger.LogInformation("Host created.");
		
		return host.RunAsync();
	}
}
```

Logging without a Generic Host:
```cs
class Program {
	static void Main(string[] args) {
		using var loggerFactory = LoggerFactory.Create(builder => {
			builder
				// Filters are invoked for all providers that do not have rules assigned to them:
				.AddFilter("SomeCategory", LogLevel.Warning)
				.AddFilter("OtherCategory", LogLevel.Information)
				.AddFilter("Namespace.Program", LogLevel.Debug)
				.AddConsole();
		});
		
		ILogger logger = loggerFactory.CreateLogger<Program>();
		logger.LogInformation("Log message.");
	}
}
```

# Configuration [[Documentation](https://docs.microsoft.com/en-us/dotnet/core/extensions/logging?tabs=command-line#set-log-level-by-command-line-environment-variables-and-other-configuration)]  
```json
{
    "Logging": { // This is the "Logging" property.
        "LogLevel": { // These are global settings.
            "Default": "Error",
            "Microsoft": "Warning"
        },
        "Debug": { // The "Debug" provider has two categories: "Default" and "Microsoft.Hosting".
            "LogLevel": { // These settings override the global settings above.
                "Default": "Information", // Use the "Information" log level for every category except
				 		   // "Microsoft.Hosting" below.
                "Microsoft.Hosting": "Trace"
            }
        },
        "EventSource": {
            "LogLevel": {
                "Default": "Warning"
            }
        }
    }
}
```

## reloading configuration
To reload configuration that changed in code while the app is running, call `IConfigurationRoot.Reload`.

# creating logs
Retrieve an `ILogger<T>` from DI:
```cs
public sealed class Worker : BackgroundService
{
    private readonly ILogger<Worker> _logger;

    public Worker(ILogger<Worker> logger) =>
        _logger = logger;

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogInformation("Worker running at: {time}", DateTimeOffset.UtcNow);
            await Task.Delay(1_000, stoppingToken);
        }
    }
}
```

## log level extension methods
`ILogger` has extension methods:
```cs
_logger.Log(LogLevel.Information, …);
// …is equivalent to…
_logger.LogInformation(…);
```

# logging features
## categories
`ILogger<T>`'s category is an arbitrary string (by convention it is the class name). The category is included with each message of that `ILogger` instance:
```cs
namespace Example;

public class DefaultService : IService {
    private readonly ILogger<DefaultService> _logger;
    
    public DefaultService(ILogger<DefaultService> logger) =>
        _logger = logger;
        // ...
    }
}
```

To explicitly specify the category:
```cs
public class DefaultService : IService {
    private readonly ILogger _logger;

    public DefaultService(ILoggerFactory loggerFactory) =>
        _logger = loggerFactory.CreateLogger("CustomCategory");
}
```
`ILogger<T>` is equivalent to calling `CreateLogger(T).`

## event ids
> Documentation: https://docs.microsoft.com/en-us/dotnet/core/extensions/logging?tabs=command-line#log-event-id  

An `EventId` is a struct with an `Id` and optional `Name` readonly properties.  The event ID can associate a set of events.

The `Debug` provider does not show event IDs.  The `Console` provider shows event IDs in brackets after the category: 
```posh
info: Example.DefaultService.GetAsync[1001]
```

### using event ids
Create a class like this:
```cs
internal static class AppLogEvents
{
    internal EventId Create = new(1000, "Created");
    internal EventId Read = new(1001, "Read");
    internal EventId Update = new(1002, "Updated");
    internal EventId Delete = new(1003, "Deleted");
    // ...
}
```

The `Log*` methods have overloads to accept an event ID:
```cs
_logger.LogWarning(AppLogEvents.ReadNotFound, "GetAsync({Id}) not found", id);
```

<o>Note</o>: The `Debug` logging provider does not show event IDs.

## exceptions
The logger methods have overloads that take an exception parameter:
```cs
catch (Exception ex)
{
    _logger.LogWarning(
        AppLogEvents.Error, ex,
        "Failed to process iteration: {Id}", id);
}
```

## filters 
> Documentation: https://learn.microsoft.com/en-us/dotnet/core/extensions/logging?tabs=command-line#how-filtering-rules-are-applied  
> Documentation: https://learn.microsoft.com/en-us/dotnet/core/extensions/logging?tabs=command-line#filter-function  

When an `ILogger<T>` object is created, `ILoggerFactory` selects a single rule per provider to apply to that logger. Messages written by that instance are filtered based on the rule. The most specific rule for each provider and category pair is selected.

## message templates
- Log APIs use a message template that can contains placeholders for arguments provided.
- This enables logging providers to implement structured (semantic) logging.
- This also allows you to avoid the use of string interpolation which has performance consequences.
- Documentation: https://docs.microsoft.com/en-us/dotnet/core/extensions/logging?tabs=command-line#log-message-template

```cs
int value1 = 3;
int value2 = 9;
_logger.LogInformation("Values: {v2}, {v1}", value1, value2); // output: 3, 9
```

<o>Use the above technique instead of string interpolation to avoid performance problems.</o>

### formatting message templates
Log message templates utilize the base [formatting types](https://learn.microsoft.com/en-us/dotnet/standard/base-types/formatting-types):

```cs
_logger.LogInformation("Logged on {PlaceHolderName:MMMM dd, yyyy}", DateTimeOffset.UtcNow); // Logged on January 06, 2022
```

Message templates also support the `@` structure capturing operator.  This allows you to log the values of an object's properties:  
```cs
Person person = new Person() { FirstName = "John", LastName = "Doe" };
_logger.LogInformation("Found {@Person}", person); // output: Found Person { FirstName="John", LastName="Doe" }
```

## log scopes 
> Documentation: https://docs.microsoft.com/en-us/dotnet/core/extensions/logging?tabs=command-line#log-scopes

A scope groups a set of logical operations.  For example, every log created as part of processing a transaction can include the transaction ID.

Scopes are supported by the `Console`, `AzureAppServicesFile`, and `AzureAppService`'s Blob providers.

# no async methods
Logging should be so fast that it is not worth the performance cost of asynchronous code.

# creating logs in main
Get an `ILogger` instance from DI immediately after building the host:
```cs
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;
using Microsoft.Extensions.Logging;

using IHost host = Host.CreateApplicationBuilder(args).Build();

var logger = host.Services.GetRequiredService<ILogger<Program>>();
logger.LogInformation("Host created.");

await host.RunAsync();
```
