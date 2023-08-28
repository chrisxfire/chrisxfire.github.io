---
title: cancellation
date: 2022-02-16T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Cancellation allows asynchronous or long-running operations to stop cleanly.

Some objects invoke long-running, cancelable operations. These objects can pass a `CancellationToken` to those downstream operation. Downstream operations can pass that same token to other operations. When the cancellation token is invoked, it is a *cancellation request*; it means that the operation should stop as soon as possible after any required cleanup is performed. A single token can cancel multiple asynchronous invocations.

# Creating
Cancellation tokens are created with `CancellationTokenSource` objects.  The CTS's `Token` property returns the `CancellationToken` (CT) that is signaled when the CTS's `Cancel` method is called:
```cs
var cts = new CancellationTokenSource();
string result = await DownloadStringTaskAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

`CancellationTokenSource` is disposable.

# Listening for and Processing Cancellation
`CancellationToken` has its `IsCancellationRequested` property set to `true` once `Cancel` is called on the CTS.  Poll this value at interval to check for a cancellation request.

This property can only be set once, so the CT cannot be reused after being canceled.

After receiving a cancellation request, perform cleanup, then either:
1. return, or;
2. call `CancellationToken.ThrowIfCancellationRequest()`.

Option 2 throws an `OperationCanceledException`. This exception can be caught by upstream operations to signal that cancellation was requested downstream.

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

# Registering Callbacks for Cancellation Requests
> Documentation: https://learn.microsoft.com/en-us/dotnet/standard/threading/cancellation-in-managed-threads#listening-by-registering-a-callback
> Documentation: https://learn.microsoft.com/en-us/dotnet/standard/threading/how-to-register-callbacks-for-cancellation-requests

You can register a delegate that is invoked when `Cancel` is called on a `CancellationToken`:
```cs
public void SomeMethod(CancellationToken token)
{
    // ...do some work...
    token.Register(() => 
    {
        Console.WriteLine("Cancellation requested!");
        CancelMethod();
    });
}

public void CancelMethod() 
{
    // clean up work...
}
```

Even if cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.