---
title: serilog
date: 2021-12-11T13:17:43-0700
draft: false
---
# [Serilog](https://serilog.net/)
Structured event logging.
Github: [Getting Started · serilog/serilog Wiki (github.com)](https://github.com/serilog/serilog/wiki/Getting-Started)  

```powershell
dotnet add package serilog
```

[dotnet add package serilog.sinks.console](https://github.com/serilog/serilog-sinks-console)Pretty print to console.  
[dotnet add package serilog.sinks.file](https://github.com/serilog/serilog-sinks-file)Log to file.  

Other Sinks Available: <https://github.com/serilog/serilog/wiki/Provided-Sinks>

# Creating Loggers
```cs
Serilog.Core.Logger
Serilog.Ilogger
Serilog.Log
```

## Create Root Logger
Create this on application startup and then use it across classes:
```cs
using var log = new LoggerConfiguration()
  .MinimumLevel.Debug() // The minimum log level. If not specified, Information is used.
  .WriteTo.Console( // The WriteTo object configures sinks.
    AnsiConsoleTheme.Code, // 256-color VS Code inspired theme.
                           // Also: ConsoleTheme.None, SystemConsoleTheme.Literate (default), SystemConsoleTheme.Grayscale
    outputTemplate: "[{Level:u3}] [{Timestamp: HH:mm:ss}] {Message}{Newline}{Exception}")
  .WriteTo.File("path",
    new CompactJsonFormatter(), // Emit output as JSON instead of plaintext. See also: https://github.com/serilog/serilog/wiki/Formatting-Output#formatting-json
    rollingInterval: RollingInterval.Day,
    fileSizeLimitBytes: n, // Override the default (1GB) file size limit.
    retainedFileCountLimit: n, // Override the default (31) number of log files to keep.
    rollOnFileSizeLimit: true // Force roll over if the file size limit is met.
    outputTemplate: "{Timestamp:yyyy-MM-dd HH:mm:ss.fff zzz} [{Level:u3}] {Message:lj}{NewLine}{Exception}"),
    Message:lj // Output (l)iterals as is, the rest in (j)son.
    Level:u3 // Output the level names as 3-character (u)ppercase. Or: lo(w)ercase.
    Properties:j // Output additional context information as (j)son (or omit (j) for plain text).
    restrictedToMinimumLevel: LogEventLevel.Information) // Override the minimum debug level. Must be higher than the Logger's level.
  .CreateLogger();
```

## Set the Global, Statically-Accessible Logger
This is not required.
```cs
Log.Logger = log;
```

# [Use the Logger](https://github.com/serilog/serilog/wiki/Writing-Log-Events)
```cs
log.Information("Log entry");
```

# [Log Structured Data](https://github.com/serilog/serilog/wiki/Structured-Data)
```cs
var count = 456;
Log.Information("Retrieved {Count} records", count);
```
Output: `{ "Count": 456 }`

```cs
var fruit = new[] { "Apple", "Pear", "Orange" };
Log.Information("In my bowl I have {Fruit}", fruit);
```
Output: `{ "Fruit": ["Apple", "Pear", "Orange"] }`

## Destructuring
Use `@` operator to pull values out of structured data:  
```cs
var sensorInput = new { Latitude = 25, Longitude = 134 };  
Log.Information("Processing {@SensorInput}", sensorInput);  

// Extract only a subset of properties from a complex object:
Log.Logger = new LoggerConfiguration()
  .Destructure.ByTransforming<HttpRequest>(
    r => new { RawUrl = r.RawUrl, Method = r.Method })
    .WriteTo...
```

## Forcing Stringification
Use `$` operator to convert the property value to a string before any other processing takes place:
```cs
var unknown = new[] { 1, 2, 3 }
Log.Information("Received {$Data}", unknown); // Output: "System.Int32[]"
```

## Output Templates
Log output templates are used by text-based sinks like console and file.  
They are a superset of .NET format strings. Any valid `string.Format()` is accepted.

Built-in properties:  
`{Property:format specifier}`  

`Exception` - Full exception message and stack trace, multiple lines. Empty if no exception for the event.
- `Level` - The log event level as the full level name.
- `:u` letter level, uppercase.
- `:w` letter level, lowercase.

`Message`
- `:l` - Disables quoting of strings.
- `:j` - Use JSON-style rendering for any structured data.
- `NewLine` - System.Environment.NewLine

`Properties` - All other event properties that do not appear elsewhere in the output.
- `:j`
- `Timestamp` - As a DateTimeOffset

Tips
- Escape `{` with another `{`
- Name properties (like `Count` above) with PascalCase.
- Log messages in fragments; avoid periods at end when possible.
- Don't:
  - `Log.Information("The time is " + DateTime.Now);` This degrades performance and consumes cache memory.
- Do:
  - `Log.Information("The time is {Now}", DateTime.Now);`

# Shutdown
```cs
log.CloseAndFlush();
```

# [AppSettings Configuration](https://github.com/serilog/serilog/wiki/AppSettings)
XML config file based configurations.

## Installation
```powershell
dotnet add package serilog.settings.appsettings
```

## Reading Config File
```cs
Log.Logger = new LoggerConfiguration()
  .ReadFrom.AppSettings()
  // … Other configuration
  .CreateLogger();
```

# See Also
## [Enrichers](https://github.com/serilog/serilog/wiki/Enrichment)
Enrichers enrich a log event with properties of (like attaching a thread ID).

## [For Web Apps (ASP.NET)](https://github.com/serilog/serilog-aspnetcore#serilogaspnetcore---)

## Logging Levels
- `Verbose` - The noisiest; rarely used in production applications
- `Debug` - detailed information typically of use only when diagnosing problems
- `Information` - confirmation that things are working as expected
- `Warning` - an indication that something unexpected happened, or indicative of some problem in the near future (e.g.: "disk space low"); the software is still working as expected
- `Error` - due to a more serious problem, the software has not been able to perform some function
- `Fatal` - a serious error indicating that the software itself may be unable to continue running 

## Markers
[>] Start  
[·] Debug  
[-] Info  
[] Notice (WARN)  
[#] Error  
[!] Critical  
[<] End  
[?] Input  

