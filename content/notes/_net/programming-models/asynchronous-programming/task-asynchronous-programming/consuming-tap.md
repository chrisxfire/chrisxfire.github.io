---
title: consuming tap
date: 2022-11-21T22:06:24-0700
draft: false
weight: 1
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern)  

In this pattern, callbacks achieve waiting without blocking. Language-based async support hides the callbacks.

# Await keyword
The `await` keyword suspends execution. It installs a callback by using continuation. The callback resumes the async method at the point of suspension. 

When the async method is resumed:
- If operation completed successfully and was a `Task<TResult>`, then `TResult` is returned.
- If awaited task ended in `Canceled` state, an `OperationCanceledException` is thrown.
- If awaited task ended in `Faulted` state, the exception that caused the fault is thrown.
  - If multiple exceptions caused the fault, the `Task.Exception` property holds an `AggregateException` of all errors.
- When awaiting a `Task`, the await expression is of type `void`.
- When awaiting a `Task<TResult>`, the await expression is of type `TResult`.

If a `SynchronizationContext` is associated with the thread that was executing the async method when it was suspended, the async method 
resumes on that same synchronization context using that context's `Post` method. Otherwise, it relies on the task scheduler that was current
at the time of suspension. The task scheduler decides whether the awaited async operation should resume where it completed or whether the
resumption should be scheduled. 

Suspension and resumption can be configured:
- With `Task.Yield` to introduce a yield point in the async method
    ```cs
    public class Task : …
        {
            public static YieldAwaitable Yield();
            …
        }
    ```
- With `Task.ConfigureAwait` to inform the await operation not to capture and resume on the context, but to continue execution wherever the async operation that was being awaited completed:
    ```cs
    await someTask.ConfigureAwait(continueOnCapturedContext:false);
    ```

# Cancellation
Cancellation tokens are created with `CancellationTokenSource` objects. The CTS's `Token` property returns the cancellation token that is signaled when the CTS's `Cancel` method is called:
```cs
var cts = new CancellationTokenSource();
string result = await DownloadStringTaskAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

A single token can cancel multiple asynchronous invocations.

Pass `CancellationToken.None` to a method to indicate that cancellation will never be requested. The method will then optimize.

# Monitoring Progress
Some async methods expose progress through a progress interface passed into the method.

# Built-in Task-based Combinators
Use these methods for composing and working with tasks.

## `Task.Run`
The `Task.Run(Func<Task>)` overload allows you to use await within the offloaded work. This is equivalent to using `TaskFactory.StartNew` and `Unwrap` in the Task Parallel Library:
```cs
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = `await DownloadFirstImageAsync()`)
        using(Bitmap bmp2 = `await DownloadSecondImageAsync()`)
        return Mashup(bmp1, bmp2);
    });
}
```

## `Task.FromResult`
Use when data may already be available and just needs to be returned from a task-returning method:
```cs
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ? Task.FromResult(cachedValue) : GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key) { … }
```

## `Task.WhenAll`
Use to asynchronously wait on multiple tasks:
```cs
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {  
        … // work with faulted and faulted.Exception
    }
}
```

## `Task.WhenAny`
Use when you need just one of multiple async operations to complete.

### `Task.WhenAny` Use Case — Redundancy
Perform an operation multiple times and select the one that completes first:
```cs
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};

while (recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

### `Task.WhenAny` Use Case — Interleaving
Launching multiple operations and waiting for them all to complete, but processing them as they finish:
```cs
List<Task<Bitmap>> imageTasks = (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();

while (imageTasks.Count > 0) // Loop until no imageTasks remain
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks); // When one finishes…
        imageTasks.Remove(imageTask); // …remove it from the list.

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch 
    {

    }
}
```

### `Task.WhenAny` Use Case - Throttling [[Documentation](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern#throttling)]  

### `Task.WhenAny` Use Case - Early Bailout [[Documentation](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern#early-bailout)]  

## `Task.Delay`
Use to introduce pauses into an async method's execution.   
Use in combination with `Task.WhenAny` to implement a time-out:
```cs {hl_lines=8}
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);

        if (download == await Task.WhenAny(download, Task.Delay(3000))) 
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

# Custom Task-based Combinators
## `RetryOnFault` Helper Method
Retry an operation if the previous attempt fails:
```cs
public static async Task<T> RetryOnFault<T>(Func<Task<T>> function, int maxTries)
{
    for (int i=0; i<maxTries; i++)
    {
        try
        {
            return await function().ConfigureAwait(false);
        }
        catch
        {
            if (i == maxTries - 1)
                throw;
        }
    }
    return default(T);
}
```

## `NeedOnlyOne` Helper Method
Launch multiple operations, wait for any of them, then cancel the rest:
```cs
public static async Task<T> NeedOnlyOne(params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
    select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);

    cts.Cancel();

    foreach (var task in tasks)
    {
        var ignored = task.ContinueWith(t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }

    return completed;
}
```

Use the method:
```cs
double currentPrice = await NeedOnlyOne(
ct => GetCurrentPriceFromServer1Async("msft", ct),
ct => GetCurrentPriceFromServer2Async("msft", ct),
ct => GetCurrentPriceFromServer3Async("msft", ct));
```

## `WhenAllOrFirstException` Helper Method
Wait for all tasks to complete, unless one faults, then stop waiting immediately:
```cs
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);

        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);

    return tcs.Task;
}
```

# Building Task-Based Data Structures
Example custom task-based data structures include `AsyncCache` and `AsyncProducerConsumerCollection`.
> Documentation: https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern#building-task-based-data-structures