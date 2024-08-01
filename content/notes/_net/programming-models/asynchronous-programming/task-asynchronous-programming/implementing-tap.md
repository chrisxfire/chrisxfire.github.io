---
title: implementing tap
date: 2022-11-21T22:06:15-0700
draft: false
weight: 1
---

# Overview [[Documentation](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern)]  

The TAP pattern can be implemented via the C# compiler, manually, or in a hybrid of both.

# Creating TAP Methods
## Compiler Approach
Create TAP methods by using the `async` keyword. Compiler will automatically perform necessary transformations to implement TAP.
- TAP methods must return `Task` or `Task<T>`.
- Any exceptions that go unhandled in body of task are marshalled to the output task and task ends in `Faulted` state.
  - Except when an `OperationCanceledException` goes unhandled; then task ends in `Canceled` state.

## Manual Approach
1. Create a `TaskCompletionSource<TResult>` object
2. Perform the async operation
3. When the async operation completes, call `{Try}SetResult`, `{Try}SetException`, or `{Try}SetCanceled`
4. Return the resulting task

Example:
```cs
public static Task<int> ReadTask(this Stream stream, byte[] buffer, int offset, int count, object state)
{
    var tcs = new TaskCompletionSource<int>(); // #1
    stream.BeginRead(buffer, offset, count, ar => // #2
    {
        try { 
            tcs.SetResult(stream.EndRead(ar)); // #3
        }
        catch (Exception exc) { 
            tcs.SetException(exc); 
        }
    }, state);

    return tcs.Task; // #4
}
```

## Hybrid Approach
This method verifies arguments outside the compiler-generated async method:
```cs
public Task<int> MethodAsync(string input)
{
    if (input == null) 
        throw new ArgumentNullException("input");
    
    return MethodAsyncInternal(input);
}

private async Task<int> MethodAsyncInternal(string input)
{
    // code that uses await goes here

    return value;
}
```
# Workloads
If a method is purely computational, it should be exposed only as a synchronous operation.  
If a method is I/O bound, it should be exposed only as an asynchronous operation.  

## Compute-bound Tasks
- Use `Task.Run` (a shortcut to `TaskFactory.StartNew` which is no longer recommended). Tasks created this way target the thread pool.
  - Use `TaskFactory.StartNew` only when fine-grained control is required.
- Use constructors of `Task` type or the `Start` method to generate and schedule a task separately.
  - Public method must only return tasks that have been started.
- Use overloads of `Task.ContinueWith` method which creates a new task that is scheduled when another completes.
- Use `TaskFactory.ContinueWhenAll` and `ContinueWhenAny` to create a new task that is scheduled when all/any of the supplied tasks complete.

### Cancellation in Compute-bound Tasks
In compute-bound tasks, a `CancellationToken` can be passed to the async code that monitors for the token, or the `Run` or `StartNew` methods.

Example
```cs
// This task renders an image.
internal Task<Bitmap> RenderAsync(ImageData data, CancellationToken cancellationToken)
{
    return Task.Run(() =>
    {
        var bmp = new Bitmap(data.Width, data.Height);
        for (int y = 0; y < data.Height; y++)
        {
            // At each iteration, it polls the cancellation token and throws if cancellation is requested.
            cancellationToken.ThrowIfCancellationRequested();
            for (int x = 0; x < data.Width; x++)
            {
                // render pixel [x,y] into bmp
            }
        }
        return bmp;
    }, cancellationToken);
}
```

Compute-bound tasks end in `Canceled` if:
1.  Cancellation request arrives before task moves to `Running` state, or
2.  An `OperationCanceledException` goes unhandled in the body of the task, that exception contains the same `CancellationToken` that is passed in, and the token shows cancellation is requested.

If another exception goes unhandled in body of task, task ends in `Faulted` state.
- Any attempts to await task or access its result causes an exception to be thrown.

## IO-bound Tasks [[Documentation](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern#io-bound-tasks)]  

Use `TaskCompletionSource<TResult>` to create a task that is not backed by a thread for its entire execution.
- Exposes a Task property and returns a `Task<TResult>` instance.
- Lifecycle controlled by methods on the type such as `SetResult`, `SetException`, `SetCanceled`.

## Mixed (Compute-bound and I/O-bound)
```cs
public async Task<Bitmap> DownloadDataAndRenderImageAsync(CancellationToken cancellationToken)
{
    var imageData = await DownloadImageDataAsync(cancellationToken); // I/O-bound
    return await RenderAsync(imageData, cancellationToken); // Compute-bound
}
```
