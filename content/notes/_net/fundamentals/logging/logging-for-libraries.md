---
title: logging for libraries
date: 2023-08-20T00:00:00-06:00
draft: false
weight: 1
---

# Overview [[Documentation](https://learn.microsoft.com/en-us/dotnet/core/extensions/logging-library-authors)]  

These notes provide guidance on exposing logging in a library in a way that is consistent with other .NET libraries and frameworks.

# `ILoggerFactory` vs. Injecting `ILogger<T>`
- When you need a logger object that can be passed on to multiple classes in the library, use `ILoggerFactory`.
- When you need a logger object that is only used in one class and never shared, use a constructor-injected `ILogger<T>`.

# Prefer Source-Generated Logging
```cs
// This partial class is static so it can be used to create extensions on ILogger:
internal static partial class LogMessages
{
    // The source-generated LoggerMessageAttribute:
    [LoggerMessage(
        Message = "Sold {quantity} of {description}",
        Level = LogLevel.Information)]
    internal static partial void LogProductSaleDetails(
        this ILogger logger,
        int quantity,
        string description);
}
```

# Use the Null Logger and No-Op Logging Defaults
Consider an example service that takes an `ILogger` as a parameter:
```cs
public class SomeService
{
    private readonly ILogger _logger;

    public SomeService(ILogger logger = null)
    {
        _logger = logger ?? NullLogger.Instance;
    }

    public void DoSomething(string message)
    {
        _logger.LogTrace("Doing something: {Message}", message);
        // ...
    }
}
```

In the above example:
- The constructor uses a default value of `null` in the event that no `ILogger` is provided.
- The null-coalescing operator is used to assign either a valid `ILogger` or a `NullLogger.Instance` to `_logger`.
- The `LogTrace` call is a no-op if the `NullLogger` is used. 

`NullLogger` is also generic and can be passed as `NullLogger<ServiceType>.Instance`.