---
title: notes > .net > async programming > tap (async await) > overview
date: 2022-11-21T21:16:58-0700
draft: false
---
# Task-based Asynchronous Pattern
- Returns Task or Task<T>
- Async methods should only do a minimal amount of synchronous work
- Exceptions that occur when an async method is running should be assigned to returned task.

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

# [Progress](https://learn.microsoft.com/en-us/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap#progress-reporting-optional)
