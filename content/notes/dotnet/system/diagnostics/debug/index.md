---
title: "notes > dotnet > system > diagnostics > debug"
date: 2021-12-15T14:32:47-0700
draft: true
---
# [Debug](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.debug?view=net-6.0)
Prefer `ILogger` over `System.Diagnostics.Debug` and `System.Diagnostics.Trace`.
Methods and properties to debug code.
This class can only be used when the application is compiled in DEBUG mode.
Object –> Debug

# Enabling Debugging
Either:
1.  Add #define DEBUG (or #define TRACE) to the top of the file, or;
2.  Add the /d:DEBUG or /d:TRACE flag when compiling.

# Adding Trace Listeners
Trace Listeners are shared by both Debug and Trace and used to output debug/trace information:

## Using a TextWriterTraceListener
Debug.Listeners.Add(new TextWriterTraceListener(Console.Out));
Debug.AutoFlush = true;
Debug.WriteLine("*message*");

## Using DefaultTraceListener
Trace.Listeners.Clear(); // Remove the default trace listener.
DefaultTraceListener defaultListener = new();
Trace.Listeners.Add(defaultListener); // This also automatically adds the listener to Debug.Listeners.
defaultListener.LogFileName = *filename*;

Debug.WriteLine("*message*");