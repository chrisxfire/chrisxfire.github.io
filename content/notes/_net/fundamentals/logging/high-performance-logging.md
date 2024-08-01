---
title: high performance logging
date: 2023-08-20T00:00:00-06:00
draft: false
weight: 2
---

# Overview [[Documentation](https://learn.microsoft.com/en-us/dotnet/core/extensions/high-performance-logging)]  

High-performance logging is achieved with `LoggerMessage`. This class exposes functionality to create delegates that can be cached. This approach requires fewer object allocations and reduced computational overhead vs. `ILogger`.

# Create a logger message
`LoggerMessage.Define(LogLevel, EventId, String)` configures an `Action` delegate that represents a log message. Each log message is stored in a static field created by `Define`.

```cs
private static readonly Action<ILogger, Exception> s_failedToProcessWorkItem;
```

The delegate is assigned:
```cs
s_failedToProcessWorkItem = LoggerMessage.Define(
    LogLevel.Critical,
    new EventId(13, nameof(FailedToProcessWorkItem)),
    "Epic failure processing item!");
```

Notes:
- `Define` supports up to six type parameters.
- `Define`'s `String` parameter uses [message templates](../overview#message-templates). 

Extensions are defined:
```cs
public static class LoggerExtensions 
{
        public static void PriorityItemProcessed(this ILogger logger, WorkItem workItem) => 
            s_processingPriorityItem(logger, workItem, default!);

        public static void FailedToProcessWorkItem(this ILogger logger, Exception ex) => 
            s_failedToProcessWorkItem(logger, ex);

        public static IDisposable? ProcessingWorkScope(this ILogger logger, DateTime time) => 
            s_processingWorkScope(logger, time);
}
```

The delegates are invoked through their extension methods:
```cs
protected override async Task ExecuteAsync(
    CancellationToken stoppingToken)
{
    using IDisposable? scope = _logger.ProcessingWorkScope(DateTime.Now);

    while (!stoppingToken.IsCancellationRequested)
    {
        WorkItem? nextItem = _priorityQueue.ProcessNextHighestPriority();
        try
        {
            if (nextItem is not null)
                _logger.PriorityItemProcessed(nextItem);
        }
        catch (Exception ex)
        {
            _logger.FailedToProcessWorkItem(ex);
        }

        await Task.Delay(1_000, stoppingToken);
    }
}
```

# Logger Message Scope
Use the `DefineScope` method.   
> Documentation: https://learn.microsoft.com/en-us/dotnet/core/extensions/high-performance-logging#define-logger-message-scope

# Enhancing Further: Log Level Guarded Optimizations
Check the log level with `ILogger.IsEnabled(LogLevel)` before invoking a `Log*` method.  
> Documentation:  https://learn.microsoft.com/en-us/dotnet/core/extensions/high-performance-logging#log-level-guarded-optimizations