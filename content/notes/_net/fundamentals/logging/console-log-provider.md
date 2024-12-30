---
title: console log provider
date: 2023-08-20T00:00:00-06:00
draft: false
weight: 1
---

# overview
> [!IMPORTANT]
> Availability: .NET 5  

> Documentation: https://learn.microsoft.com/en-us/dotnet/core/extensions/console-log-formatter

The `Console` log provider supports three formatting options: Simple, Systemd, and Json.

# registering
To register any one of the formatters, use the `Add{TYPE}Console` extension method:
```cs
using Microsoft.Extensions.Logging;

using ILoggerFactory loggerFactory =
    LoggerFactory.Create(builder =>
        builder.AddSimpleConsole(options =>
        {
            options.IncludeScopes = true;
            options.SingleLine = true;
            options.TimestampFormat = "HH:mm:ss ";
        }));
```

## registering via configuration file
```json
{
    "Logging": {
        "LogLevel": {
            "Default": "Information",
            "Microsoft": "Warning",
            "Microsoft.Hosting.Lifetime": "Information"
        },
        "Console": {
            "LogLevel": {
                "Default": "Information",
                "Microsoft": "Warning",
                "Microsoft.Hosting.Lifetime": "Information"
            },
            "FormatterName": "json",
            "FormatterOptions": {
                "SingleLine": true,
                "IncludeScopes": true,
                "TimestampFormat": "HH:mm:ss ",
                "UseUtcTimestamp": true,
                "JsonWriterOptions": {
                    "Indented": true
                }
            }
        }
    },
    "AllowedHosts": "*"
}
```

# simple
- Can wrap information such as time and log level in each log message
- Supports ANSI color embedding
- Supports indentation fo messages

# systemd
- Uses the *syslog* standard
- Always logs messages on a single line
- No color support

# json
- Writes logs in JSON format
- By default, logs messages on a single line
  - Use `JsonWriterOptions.Indented = true` to improve readability
- <o>Do not pass in log messages that have already been serialized to JSON</o>

# custom formatters
To create a custom formatter, inherit from ConsoleFormatter and register the custom formatter.

> Documentation: https://learn.microsoft.com/en-us/dotnet/core/extensions/console-log-formatter#implement-a-custom-formatter