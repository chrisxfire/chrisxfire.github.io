---
title: patterns
date: 2022-07-21T08:27:56-0600
draft: false
weight: 1
---
Delegates support minimal coupling between components.

# example with linq where method
The `Where` method uses a delegate that determines which elements of a sequence pass the filter:
```cs
// Numbers where, for each number n, n is less than 10:
var smallNumbers = numbers.Where(n => n < 10);
```

The prototype for `Where`:
```cs
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

Loose coupling is achieved because:
- There is no need to implement an interface
- There is no need to derive from a base class

# example by building a logger
## delegate

```cs
public static class Logger 
{
    public static Action<string> WriteMessage;

    public static void LogMessage(string msg) 
    {
        // The compiler generates an `Invoke` method for any delegate type declared. This one takes a single
        // `string` argument and has a `void` return type.
        // The `?.` here prevents a `NullReferenceException` if the delegate does not have an invocation list attached.
        WriteMessage?.Invoke(msg);

        // Alternatively, without this robustness, we could use:
        // WriteMessage(msg);
    }
}
```

## implementation
```cs
// This method could be static or instance.
public static class LoggingMethods 
{
    public static void LogToConsole(string message) { Console.Error.WriteLine(message); }
}

// Attach LogToConsole to the WriteMessage delegate:
Logger.WriteMessage += LoggingMethods.LogToConsole;

## another implementation
public class FileLogger 
{
    private readonly string logPath;

    public FileLogger(string path) 
    {
    logPath = path;
    Logger.WriteMessage += LogMessage;
    }

    public void DetachLog() { Logger.WriteMessage -= LogMessage; }
    private void LogMessage(string msg) 
    {
        try
        {
            using (var log = File.AppendText(logPath)) 
            {
                log.WriteLine(msg);
                log.Flush();
            }
        }
        catch (Exception)
        {
            // Catch and drop the exception (can't log an exception that came from the logger!)
            // If any delegate method throws an exception, the remaining delegates on the invocation list will
            // not be invoked.
        }
    }
}

// When `FileLogger` is called, it attaches its `LogMessage` method to the `WriteMessage` delegate:
var file = new FileLogger("log.txt");
```
