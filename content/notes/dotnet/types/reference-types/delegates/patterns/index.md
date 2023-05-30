---
title: "notes > dotnet > types > reference types > delegates > patterns"
date: 2022-07-21T08:27:56-0600
draft: true
---
Delegates support minimal coupling between components.

# Example with LINQ Where Method
The `Where` method uses a delegate that determines which elements of a sequence pass the filter:
// Numbers where, for each number *n*, *n* is less than 10:
var smallNumbers = numbers.Where(n => n < 10);

The prototype for `Where`:
public static IEnumerable<TSource> Where<TSource> (this IEnumerable<TSource> source, Func<TSource, bool> predicate);

Loose coupling is achieved because:
- There is no need to implement an interface
- There is no need to derive from a base class

# Example by Building a Logger
## Delegate
public static class Logger {
public static Action<string> WriteMessage;

public static void LogMessage(string msg) {
// The compiler generates an `Invoke` method for any delegate type declared. This one takes a single
// `string` argument and has a `void` return type.
// The `?.` here prevents a `NullReferenceException` if the delegate does not have an invocation list attached.
WriteMessage?.Invoke(msg);

// Alternatively, without this robustness, we could use:
// WriteMessage(msg);
}
}

## Implementation
// This method could be static or instance.
public static class LoggingMethods {
public static void LogToConsole(string message) { Console.Error.WriteLine(message); }
}

// Attach LogToConsole to the WriteMessage delegate:
Logger.WriteMessage += LoggingMethods.LogToConsole;

## Another Implementation
public class FileLogger {
private readonly string logPath;

public FileLogger(string path) {
logPath = path;
Logger.WriteMessage += LogMessage;
}

public void DetachLog() { Logger.WriteMessage -= LogMessage; }
private void LogMessage(string msg) {
try
{
using (var log = File.AppendText(logPath)) {
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


