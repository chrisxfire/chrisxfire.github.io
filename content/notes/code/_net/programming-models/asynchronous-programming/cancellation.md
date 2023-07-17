---
title: notes > code > .net > programming models > asynchronous programming > cancellation
date: 2022-02-16T00:00:00-06:00
draft: false
weight: 1
---

# Cancellation
Cancellation tokens are created with `CancellationTokenSource` objects.  The CTS's Token property returns the cancellation token that is signaled when the CTS's Cancel method is called:
```cs
var cts = new CancellationTokenSource();
string result = await DownloadStringTaskAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

A single token can cancel multiple asynchronous invocations.

# Disposable
`CancellationTokenSource` is disposable.

# Listening for and Processing Cancellation
`CancellationToken` has its `IsCancellationRequested` property set to true once Cancel is called on the CTS.  Poll this value at interval to check for a cancellation request.

This property can only be set once, so the CT cannot be reused after being canceled.

After receiving a cancellation request, perform cleanup then call `CancellationToken.ThrowIfCancellationRequest()`.

Pass `CancellationToken.None` to a method to indicate that cancellation will never be requested.  The method will then optimize.

# Canceling Tasks After a Period of Time
Use `CancellationTokenSource`'s `CancelAfter` method to schedule the cancellation of any tasks that are not complete within a period of time:
```cs
static async Task Main()
{
    Console.WriteLine("Application started.");

    try
    {
        s_cts.CancelAfter(3500); // 3500 milliseconds

        await SumPageSizesAsync();
    }
    catch (OperationCanceledException) // An OCE is thrown when a cancellation is triggered.
    {
        Console.WriteLine("\nTasks cancelled: timed out.\n");
    }
    finally
    {
        s_cts.Dispose();
    }

    Console.WriteLine("Application ending.");
}
```
