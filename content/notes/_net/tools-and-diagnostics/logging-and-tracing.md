---
title: logging and tracing
date: 2023-08-18T00:00:00-06:00
draft: false
weight: 1
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/core/diagnostics/logging-tracing)  

These notes discuss the differences between logging and tracing and the differences between the many logging APIs available in .NET.

# Logging vs. Tracing
Both logging and tracing serve as a record of interesting events that occur while a program is running. 
- *Logging* is expected to be collected all the time and should have low overhead. 
  - *Unstructured logging* yields log entries that have free-form text content.
  - *Structured logging* yields log entries with well-defined schema and can be encoded in different machine-readable formats.
- *Tracing* is usually more invasive and collects more information and should be collected for short periods of time.
- *Distributed tracing* collects high-level activity and timing data for request-based systems and correlates the requests across services to give a holistic view of the system.

Also:  
- *Sinks* are logging destinations. Many logging APIs have pre-built sinks.

# .NET Logging APIs
## `ILogger`
The best default choice:
- Supports structured logging
- Flexible configuration
- Contains a common sinks
- Serves as a facade over 3rd-party implementations

## `EventSource`
An order, high-performance tracing API with structured logging:
- Integrates with [Event Tracing for Windows (ETW)](https://learn.microsoft.com/en-us/windows/win32/etw/event-tracing-portal)
- Extended to support [EventPipe](https://learn.microsoft.com/en-us/dotnet/core/diagnostics/eventpipe) for cross-platform tracing and `EventListener` for custom sinks
- <o>Fewer built-in logging sinks than `ILogger`</o>
- <o>No configuration file support</o>

## `Trace`
Includes `System.Diagnostics.Trace` and `System.Diagnostics.Debug`:
- Legacy
- Best used for .NET Framework (not .NET Core)

## comparison
| Logging API   | Structured logging? | Configuration file support?        | Common sinks? |
| ------------- | ------------------- | ---------------------------------- | ------------- |
| `ILogger`     | Yes                 | Yes                                | Yes           |
| `EventSource` | Yes                 | <r>No</r>                          | <r>No</r>     |
| `Trace`       | <r>No</r>           | <r>No</r> (only in .NET Framework) | Yes           |

# Specialized .NET Logging APIs
## `Console`
Uses `System.Console`'s `Write` and `WriteLine` methods:
- No structured logging support 
- Not flexible
- No configuration file support
- No sink support
- Best used with `ILogger` or `Trace` APIs with a console sink

## `DiagnosticSource`
`System.Diagnostic.DiagnosticSource` is for logging where messages will be analyzed synchronously and not persisted to storage:
- Allows source and listener to exchange .NET objects as messages
- Very fast if listener implemented correctly (tens of nanoseconds)

## `EventLog`
`System.Diagnostics.EventLog` is for logging to the Windows Event Log:
- Use `ILogger` with an optional `EventLog` sink.

# Tracing (`Debug` & `Trace`)
Use methods in the `System.Diagnostics.Debug` class to print debugging information and check logic with assertions.  
Customize `Debug` and `Trace` output by adding a `System.Diagnostics.TraceListener` to the `System.Diagnostics.Listeners` collection.
- The `Listeners` collection is shared by both `Debug` and `Trace.`

If using Visual Studio:
- The DEBUG conditional compilation symbol is defined for debug builds
- The TRACE symbol is defined for both debug and release builds.

This means that, by default, debugging is enabled on debug builds, and debugging and tracing is enabled on both debug and release builds.

If not using Visual Studio, debugging and tracing need to be enabled manually.

`System.Diagnostics.Debug` is type safe.

## Example [[Documentation](https://learn.microsoft.com/en-us/dotnet/api/system.diagnostics.defaulttracelistener?view=net-7.0#remarks)]  

```cs
public static void Main(string[] args)
{
  // Remove the original default trace listener.
  Trace.Listeners.RemoveAt(0);

  // Create and add a new default trace listener.
  DefaultTraceListener defaultListener = new DefaultTraceListener();
  Trace.Listeners.Add(defaultListener);

  // Assign the log file specification from the command line, if entered.
  if (args.Length>=2)
  {
    defaultListener.LogFileName = args[1];
  }
```

## TextWriterTraceListener [[Documentation](https://learn.microsoft.com/en-us/dotnet/api/system.diagnostics.textwritertracelistener?view=net-7.0#remarks)]  

Directs tracing or debugging output to a `TextWriter` or a `Stream`. <o>Implements `IDisposable`.</o>
```cs
public static int Main(string[] args) 
{
    // Create a file for output named TestFile.txt.
    Stream myFile = File.Create("TestFile.txt");

    /* Create a new text writer using the output stream, and add it to the trace listeners. */
    TextWriterTraceListener myTextListener = new TextWriterTraceListener(myFile);
    Trace.Listeners.Add(myTextListener);

    // Write output to the file.
    Trace.Write("Test output ");

    // Flush the output.
    Trace.Flush();

    return 0;
}
```