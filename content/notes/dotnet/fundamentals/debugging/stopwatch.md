---
title: stopwatch
date: 2021-12-24T15:52:31-0700
draft: false
weight: 1
---
# [Stopwatch](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.stopwatch?view=net-6.0)
`Object` –> `Stopwatch`  

# Example
```cs
Stopwatch sw = new Stopwatch();
sw.Start();
// …
sw.Stop();
TimeSpan ts = sw.Elapsed;
// Calling sw.Start() again here resumes the stopwatch at the elapsed time it was stopped
```

# Methods
`StartNew()` — Start a new stopwatch timer
`Reset()` — Reset a timer
`Restart()` — Reset a timer and start it

# Properties
`Elapsed`
`ElapsedMilliseconds`
`ElapsedTicks` — Ticks elapsed since stopwatch started/stopped
`Frequency` — Ticks per second
- Note: (1000L * 1000L * 1000L) / frequency = nanoseconds per tick
`IsHighResolution` — If true, using system's high-resolution performance counter. Else, DateTime class.
`IsRunning` — Boolean if stopwatch is running

# A Recorder Class to Monitor Performance
```cs
using System.Diagnostics;

public static class Recorder
{
    private static Stopwatch timer = new();
    private static long bytesPhysicalBefore = 0;
    private static long bytesVirtualBefore = 0;

    public static void Start()
    {
        // Store the current physical and virtual memory use:
        bytesPhysicalBefore = Process.GetCurrentProcess().WorkingSet64;
        bytesVirtualBefore = Process.GetCurrentProcess().VirtualMemorySize64;
        timer.Restart();
    }

    public static void Stop()
    {
        timer.Stop();
        long bytesPhysicalAfter = GetCurrentProcess().WorkingSet64;

        long bytesVirtualAfter = GetCurrentProcess().VirtualMemorySize64;

        Console.WriteLine($"{bytesPhysicalAfter - bytesPhysicalBefore}");
        Console.WriteLine($"{bytesVirtualAfter - bytesVirtualBefore}");
        Console.WriteLine($"{timer.Elapsed} elapsed.");
        Console.WriteLine($"{timer.ElapsedMilliseconds} ms elapsed.");
    }
}
```
