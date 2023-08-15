---
title: consuming tap
date: 2022-11-21T22:06:24-0700
draft: false
weight: 1
---
# Consuming the Task-based Asynchronous Pattern
In this pattern, callbacks achieve waiting without blocking. Language-based async support hides the callbacks.

# Await keyword
The `await` keyword suspends execution. It installs a callback by using continuation. The callback resumes the async method at the point of suspension. When the async method is resumed:
- If operation completed successfully and was a `Task<TResult>`, then `TResult` is returned.
- If awaited task ended in `Canceled` state, an `OperationCanceledException` is thrown.
- If awaited task ended in `Faulted` state, the exception that caused the fault is thrown.
  - If multiple exceptions caused the fault, the `Task.Exception` property holds an `AggregateException` of all errors.
- When awaiting a `Task`, the await expression is of type `void`.
- When awaiting a `Task<TResult>`, the await expression is of type `TResult`.

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
# `Task.Run`
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
# `Task.FromResult`
Use when data may already be available and just needs to be returned from a task-returning method:
```cs
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ? Task.FromResult(cachedValue) : GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key) { … }
```
# `Task.WhenAll`
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
# `Task.WhenAny`
Use when you need just one of multiple async operations to complete.

## `Task.WhenAny` Use Case — Redundancy
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
## `Task.WhenAny` Use Case — Interleaving
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
## `Task.WhenAny` Use Case — Throttling
Don't start additional operations until others complete.
