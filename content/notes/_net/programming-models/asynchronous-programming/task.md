---
title: task
date: 2022-11-23T09:58:39-0700
draft: false
weight: 1
---

# overview
In C#, `Thread` and `Task` are both types used for asynchronous operations. `Task` is a higher level of abstraction than `Thread`.

`System.Threading.Tasks` contains types for writing concurrent and asynchronous code.
- `TaskFactory` — static methods for creating and starting tasks.
- `TaskScheduler` — thread scheduling infrastructure.
- `Task` — a wrapper around a thread that enables easier management.

`System.Threading.Tasks.Extensions.ValueTask` is a lightweight implementation of a generalized task-returning value.

# `Task` and `Task<T>` [[Documentation](https://docs.microsoft.com/en-us/dotnet/api/system.threading.tasks.task?view=net-6.0)]  

`Task` represents a single asynchronous operation that does not return a value. It is a reference type (so it allocates an object on the heap). 
- `Task.CompletedTask` holds a task that is already completed. If you implement a class that must return a `Task` (equivalent to `void` in a synchronous method), return `Task.CompletedTask`.
- `Task<TResult>`'s `Result` property is of type `TResult` and holds the value the task returns.
  - It is a blocking property: accessing it before the task is finished results in blocking the currently active thread until it finishes.
  - Access the value by using `await` instead.

## task lifecycle
A task's lifecycle is represented by the [TaskStatus] enumeration and contains these states:
- (`0`) `Created` — initialized, but not yet scheduled.
- (`1`) `WaitingForActivation` — waiting to be activated and scheduled internally.
- (`2`) `WaitingToRun` — scheduled, but not yet started.
- (`3`) `Running` — started, but not yet completed.
- (`4`) `WaitingForChildrenToComplete` — completed, but waiting for attached child tasks to complete.
- (`5`) `RanToCompletion` — completed.
- (`6`) `Canceled` — either:
  - The task has acknowledged cancellation by throwing an `OperationCanceledException` with its own `CancellationToken`, or;
  - The task's `CancellationToken` was signaled before the task started.
- (`7`) `Faulted` — the task completed due to an unhandled exception.

## creating and starting
- Tasks that are created with public `Task` constructors are *cold* tasks — they are in the `Created` state. They must be `Start()`ed.
- All tasks that are returned from TAP methods must be started. 
  - If, internally, a TAP method uses a task's constructor to instantiate the task to be returned, **the TAP method must still** call `Start` on the `Task` object returned.

```cs
public static async Task Main()
{
    await Task.Run( () =>
    {
        …
    }
}
```
or, equivalently using a `TaskFactory.StartNew`, but this method is no longer recommended.

- `Task t1 = new(MethodA);` — instantiated, but not started.
  - `t1.Start()` — start the task then continue executing.
    - <o>Caution</o>: calling `Start` on an active task throws an `InvalidOperationException`. Check `Task.TaskStatus` to determine its state.
- `Task t2 = Task.Factory.StartNew(MethodB);` — instantiated and started.
- `Task t3 = Task.Run(MethodC);` — instantiated and started.

## waiting
### waiting decision table
| Goal                                     | <g>Use this</g>      | <r>Not this</r>              |
| ---------------------------------------- | -------------------- | ---------------------------- |
| Retrieve the result of a background task | `await`              | `Task.Wait` or `Task.Result` |
| Waiting for any task to complete         | `await Task.WhenAny` | `Task.WaitAny`               |
| Waiting for all tasks to complete        | `await Task.WhenAll` | `Task.WaitAll`               |
| Waiting for a period of time             | `await Task.Delay`   | `Thread.Sleep`               |

### `Task.Wait` (Blocking)
Wait to block the thread that started the Task. Otherwise, if the calling thread is the Main app thread, the app may terminate before the Task completes:
```cs
t1.Wait();
// or:
t1.Wait(n); // Wait for n milliseconds.
// or:
t1.Wait(TimeSpan)
// or:
t1.Wait(CancellationToken) // If a CancellationToken is fulfilled while waiting, OperationCanceledException is thrown.
// or:
t1.Wait(n, CancellationToken)

t4.RunSynchronously(); // Start the task on the main thread.
t4.Wait(); // Should still wait in case an error is thrown.
```

### `Task.WaitAny` (Blocking)
To wait on the first of a series of Tasks to finish:
```cs
Task.WaitAny(t1, t2, …) // WaitAny() returns the index (an Int32) of which Task in the list finished.
```

To wait on all the Tasks in a series to finish:
```cs
Task.WaitAll(t1, t2, …)
```

### `await Task.WhenAll` (Non-blocking)
```cs
public async Task<User> GetUserAsync(int userId)
{
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<IEnumerable<User>> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = new List<Task<User>>();
 
    foreach (int userId in userIds)
        getUserTasks.Add(GetUserAsync(userId));

    return await Task.WhenAll(getUserTasks);
}
```

### `await Task.WhenAny` (Non-blocking)
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

### exceptions while waiting
While waiting on one or more Tasks to complete, exceptions thrown are propagated to the thread that called the `Wait` method:
```cs
try
{
    Task.WaitAll(t1, t2, …);
}
catch (AggregateException ae)
{
    // One or more exceptions were thrown:
    foreach (var ex in ae.InnerExceptions)
    {
        // ex.GetType().Name, ex.Message
    }
}
```