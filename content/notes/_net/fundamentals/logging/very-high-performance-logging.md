---
title: very high performance logging (source generation)
date: 2023-08-20T00:00:00-06:00
draft: false
weight: 3
---

# Overview
<g>Availability: .NET 6</g>   
> Documentation: https://learn.microsoft.com/en-us/dotnet/core/extensions/logger-message-generator

The `LoggerMessageAttribute`, part of `Microsoft.Extensions.Logging`, source-generates performant logging APIs. The auto-generated code relies on `ILogger` and `LoggerMessage.Define`.

This implementation is significantly faster than [other]({{< ref "./high-performance-logging" >}}) [approaches]({{< ref "overview" >}})).

# Usage
Use `LoggerMessageAttribute` on `partial` logging methods:
```cs
public static partial class Log
{
    [LoggerMessage(
        EventId = 0,
        Level = LogLevel.Critical,
        Message = "Could not open socket to `{hostName}`")]
    public static partial void CouldNotOpenSocket(ILogger logger, string hostName);
}
```

The method does not have to be static. Example on an instance method:
```cs
public partial class InstanceLoggingExample
{
    private readonly ILogger _logger;

    public InstanceLoggingExample(ILogger logger)
    {
        _logger = logger;
    }

    [LoggerMessage(
        EventId = 0,
        Level = LogLevel.Critical,
        Message = "Could not open socket to `{hostName}`")]
    public partial void CouldNotOpenSocket(string hostName);
}
```

The log level can also be dynamically set:
```cs
public static partial class Log
{
    [LoggerMessage(
        EventId = 0,
        Message = "Could not open socket to `{hostName}`")]
    public static partial void CouldNotOpenSocket(
        ILogger logger,
        LogLevel level, /* Dynamic log level as parameter, rather than defined in attribute. */
        string hostName);
}
```

## Logging Message Constraints
Logging methods must adhere to these constraints:
1. They must be `partial` and return `void`
2. Their names cannot start with an underscore
3. Their parameter names cannot start with an underscore
4. They cannot be defined in a nested type
5. They cannot be generic