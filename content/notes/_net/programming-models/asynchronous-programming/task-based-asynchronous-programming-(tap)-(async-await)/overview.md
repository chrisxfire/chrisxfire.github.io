---
title: overview
date: 2022-11-21T21:16:58-0700
draft: false
weight: -1
---
# Task-based Asynchronous Pattern
- Returns Task or Task<T>
- Async methods should only do a minimal amount of synchronous work
- Exceptions that occur when an async method is running should be assigned to returned task.

# System.Threading.Tasks
`Object` –> `Task`  
- Types for writing concurrent and asynchronous code.
- Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.threading.tasks?view=net-6.0

## Classes
- `TaskFactory` — Static methods for creating and starting tasks.
- `TaskScheduler` — Thread scheduling infrastructure.

## Types
- `Task` — Represents an asynchronous operation that can be waited on and cancelled.
- `Task<TResult>` — A Task that can return a value.

# Task
`Object` –> `Task`  
- Represents a single asynchronous operation that does not return a value.  
- This class is a wrapper around a thread that enables easier creation and management.  
- Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.threading.tasks.task?view=net-6.0

## Construction
- `Task t1 = new(MethodA);` — Instantiated, but not started.
- `Task t2 = Task.Factory.StartNew(MethodB);` — Instantiated and started.
- `Task t3 = Task.Run(MethodC);` — Instantiated and started.

## Properties
- `CompletedTask` — Gets a task that is already completed. If you implement a class that must return a `Task` (equivalent to `void` in a synchronous method), return `Task.CompletedTask`.
- `CreationOptions`
- `Status`
- `IsCanceled`
- `IsCompleted`
- `IsFaulted`

## Methods
- `Task.Delay(n)` — Pause for n milliseconds.
- `Task.FromCanceled<TResult>(CancellationToken)` — Create a `Task<TResult>` that's completed due to cancellation within a specified cancellation token.
- `Task.FromException<TResult>(Exception)` — Create a `Task<TResult>` that's completed with a specified exception.
- `Task.FromResult<TResult>(TResult)` — Create a `Task<TResult>` whose Result property is the non-task result and whose Status property is RanToCompletion.
- `Task.WhenAll(task1, task2, …)` — Returns a `Task` that completes when all the tasks have completed.
- `Task.WaitAll(Task[] tasks)` — Returns the index of the completed task in the tasks array. The original thread pauses on the call to `WaitAll()`.
- `Task.WhenAny(task1, task2, …)` — Returns a `Task<task>` that completes when any of tasks have completed.
- `Task.WaitAny(Task[] tasks)` — Returns the index of the completed task in the tasks array.

## Starting
`t1.Start()` — The thread that started this Task will continue executing.

## Waiting
Wait to block the thread that started the Task. Otherwise, if the calling thread is the Main app thread, the app may terminate before the Task completes:
```cs
t1.Wait();
// or:
t1.Wait(n)Wait for n milliseconds.
// or:
t1.Wait(TimeSpan)
// or:
t1.Wait(CancellationToken)If a CancellationToken is fulfilled while waiting, OperationCanceledException is thrown.
// or:
t1.Wait(n, CancellationToken)

t4.RunSynchronously(); // Start the task on the main thread.
t4.Wait(); // Should still wait in case an error is thrown.
```

### Waiting on a Series of Tasks
To wait on the first of a series of Tasks to finish:
```cs
Task.WaitAny(t1, t2, …) // WaitAny() returns the index (an Int32) of which Task in the list finished.
```
To wait on all the Tasks in a series to finish:
```cs
Task.WaitAll(t1, t2, …)
```

#### Notes
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
## Creating and Executing Task Instances
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

## Wrapping Tasks Around Other Objects
- `FromResult<TResult>(TResult)` — Create a Task<TResult> object whose `Result` property is the non-task result and whose status property is `RanToCompletion`.
- `FromException<TResult>(Exception)` — Create a Task<TResult> that's completed due to an exception of the specified exception.
- `FromCanceled<TResult>(CancellationToken)` — Create a Task that's completed due to cancellation with a specified cancellation token.

# TaskStatus
- Tasks created by constructor are in `Created` status
- Calling `Start` on active task —> `InvalidOperationException`

# Cancellation
- For methods that cannot be canceled, do not provide an overload that accepts a `CancellationToken`.
- If cancellation request results in work ending prematurely, method returns Task in `Canceled` state (`IsCompleted` = true)
- Code that is asynchronously waiting for task receives a `OperationCanceledException`
- Code blocked waiting on a task through `Wait` or `WaitAll` continues to run with an exception
- If cancellation requested before TAP method starts, TAP method should return `Canceled` task
- If cancellation requested after TAP method starts, TAP method decides whether to cancel
- If cancellation requested but result/exception produced, task ends in `RanToCompletion` or `Faulted` state

# Progress Reporting
- See https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap#progress-reporting-optional
