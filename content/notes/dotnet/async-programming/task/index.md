---
title: "notes > dotnet > async programming > task"
date: 2022-11-23T09:58:39-0700
draft: false
---
# Tasks & Threads
- In C#, `Thread` and `Task` are both types. `Task` is a higher level of abstraction than `Thread`.

# Task
`Task` is a reference type (so it allocates an object on the heap).  
A task encapsulates information about the state of an asynchronous operation.

# `Task.Result`
- `Task<TResult>`'s `Result` property is of type `TResult` and holds the value the Task returns.
- It is a blocking property: accessing it before the task is finished results in blocking the currently active thread until it finishes.
  - Access the value by using `await` instead.
- Reading the `Result` property of a faulted task will throw the `AggregateException`.

# `ValueTask`
`using System.Threading.Tasks.Extensions;`
`ValueTask` is a lightweight implementation of a generalized task-returning value.

Task Decision Table
| Goal                                     | Use this           | Not this                 |
| ---------------------------------------- | ------------------ | ------------------------ |
| Retrieve the result of a background Task | await              | Task.Wait or Task.Result |
| Waiting for any task to complete         | await Task.WhenAny | Task.WaitAny             |
| Waiting for all tasks to complete        | await Task.WhenAll | Task.WaitAll             |
| Waiting for a period of time             | await Task.Delay   | Thread.Sleep             |

# `Task.WhenAll`
```cs
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}


public static async Task<IEnumerable<User>> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = new List<Task<User>>();
    foreach (int userId in userIds)
    {
        getUserTasks.Add(GetUserAsync(userId));
    }

    return await Task.WhenAll(getUserTasks);
}
```

# `Task.WhenAny`
This method accepts Task.Delay as a parameter to implement a timeout:
```cs
Task<Bitmap> download = GetBitmapAsync(url);

if (download == await Task.WhenAny(download, Task.Delay(3000)))
{
    // Downloaded the bitmap successfully
}
else
{
    // Timed out
}
```

# Helper Methods
## `RetryOnFault` Helper Method
Retry an operation if the previous attempt fails:
```cs
public static async Task<T> RetryOnFault<T>(Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
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
## `NeedOnlyOne`
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

## `WhenAllOrFirstException`
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