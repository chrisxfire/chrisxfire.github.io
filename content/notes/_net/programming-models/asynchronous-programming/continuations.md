---
title: continuations
date: 2022-11-23T00:00:00-06:00
draft: false
weight: 1
---

# continuations
- A continuation task (continuation) is an async task that is invoked by another task (the antecedent) when the antecedent finishes.
- Continuations allow descendant operations to consume the results of an ancestor.  In this way, you can chain tasks.
- A continuation is created in the WaitingForActivation state and activated automatically when its antecedent task completes.

## blocking
Continuations, like any Task, do not block the current thread.  
To block until a continuation finishes, call `Task.Wait`.

## Do Not Call Task.Start on a Continuation
This will result in an `InvalidOperationException`.

# creating a continuation for a single antecedent
Use `Task.ContinueWith`:
```cs
public class SimpleExample
{
    public static async Task Main()
    {
        // Declare, assign, and start the antecedent task.
        Task<DayOfWeek> taskA = Task.Run(() => DateTime.Today.DayOfWeek);

        // Execute the continuation when the antecedent finishes.
        var continuation = taskA.ContinueWith(antecedent => Console.WriteLine($"Today is {antecedent.Result}."));
	   await continuation;
    }
}
```

## passing data
If the antecedent user delegate is a `Task<TResult>` and it completed, then the continuation can access the `Task<TResult>.Result` property of the antecedent.  However, if the antecedent was canceled or faulted, this will throw an exception.  To avoid this, use `TaskContinuationOptions.OnlyOnRanToCompletion`:
```cs
await taskA.ContinueWith(antecedent => 
{ 
	Console.WriteLine($"Today is {antecedent.Result}.")
},  
```

Otherwise, guard against the exception.

# creating a continuation for multiple antecedents
Use `Task.WhenAll` or `Task.WhenAny` against a collection of Tasks.

# `TaskContinuationOptions`
`Task.ContinueWith` has an overload that accepts a `TaskContinuationOptions` instance.

# canceling a continuation
A continuation is canceled when:
- It receives a cancellation request and throws an `OperationCanceledException` (like any Task)
- The continuation is passed a `CancellationToken` whose `IsCancellationRequested` property is already true.
- The continuation never runs because a condition set by its `TaskContinuationOptions` was not met.

# exceptions
Exceptions thrown in continuations are not propagated back to the antecedent.  Handle them as you would in any other task.
