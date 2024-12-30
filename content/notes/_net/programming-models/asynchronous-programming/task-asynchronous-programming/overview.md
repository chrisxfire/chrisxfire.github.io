---
title: overview
date: 2022-11-21T21:16:58-0700
draft: false
weight: -1
---

# Abstract [[Documentation](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap)]  

The Task Asynchronous Pattern is a *different* pattern for using tasks, async, and await than the pattern described in [notes on asynchronous programming](../../overview).

The TAP pattern uses `Task` and `Task<T>` objects which model asynchronous operations. Generally:
- For I/O-bound code, `await` a `Task` or `Task<T>` in async method.
- For CPU-bound code, await an operation that is started on a background thread via `Task.Run`.

The TAP pattern uses a single method to represent the initiation and completion of an asynchronous operation (unlike EAP (`Begin` and `End`) and APM (`IAsyncResult`)).

# cancellation
In TAP, cancellation is optional for both async method implementers and consumers:
- Operations that may be canceled should expose an overload that accepts a `CancellationToken`. 
- Operations that cannot be canceled should not expose this overload.
- Consumer code that does not require cancellation but calls a method that exposes a cancellation token should pass a `CancellationToken.None`.

If an implemented cancellation token is signaled:
- Decision: Honor cancellation?
  - Yes
    - Return a `Canceled` state task; any code awaiting this task will receive an `OperationCanceledException`
    - Continuations scheduled?
      - Yes
        - ContinuationOption NotOnCanceled set?
          - Yes: continuations end.
          - No: continuations proceed
  - No
    - Result produced?
      - Yes: return a `RanToCompletion` state task
      - No: return a `Faulted` state task

# progress reporting
In TAP, progress is handled through the `IProgress<T>` object passed to an async method as a parameter (usually named `progress`). 
The type of `T` depends on the use case. A `ReadAsync` method may want to report the number of bytes read (as a `long`):
```cs
public Task ReadAsync(byte[] buffer, int offset, int count, IProgress<long> progress)
```

Progress reporting can be accomplished through the `Progress<T>` class which implements `IProgress<T>`. `Progress<T>` exposes a `ProgressChanged` event 
that is raised every time the async operation reports a progress update. Register a handler for this event, or pass a single handler to the `Progress<T>` constructor.

# Interop with Other Asynchronous Patterns and Types [[Documentation](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types)]  