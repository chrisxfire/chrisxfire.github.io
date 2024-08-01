---
title: await
date: 2022-02-16T00:00:00-06:00
draft: false
weight: 1
---

# Await
The `await` keyword marks a point where the method cannot continue until the awaited async operation is complete.
- It suspends this method and yields control back to the caller until then.
- It signs up the rest of the method as a continuation.
- It does not run on its own thread (unless called via `Task.Run()`).

Example
```cs
async Task<int> GetTaskOfResultAsync() {
	int hours = 0;
	await Task.Delay(0);
	return hours;
}

// This calls the async method:
Task<int> returnedTaskTResult = GetTaskOfResultAsync();
// This awaits the Task that the method returns and "unwraps" the int it holds:
int intResult = await returnedTaskTResult;
```

# Awaiting `Task.Run` or `Task`/`Task<T>`
- For I/O-bound code, await an operation that returns a `Task` or `Task<T>` inside an async method.
- For CPU-bound code, await an operation that is started on a background thread with `Task.Run`.
	- Or, consider the Task Parallel Library ([Notes on Task Parallel Library](../../parallel-programming)).

TODO: 
# Await Decision Table
The `Task.Wait`* methods are synchronous, not asynchronous.

| Goal                                     | Use this             | Not this                     |
| ---------------------------------------- | -------------------- | ---------------------------- |
| Retrieve the result of a background Task | `await`              | `Task.Wait` or `Task.Result` |
| Waiting for any task to complete         | `await Task.WhenAny` | `Task.WaitAny`               |
| Waiting for all tasks to complete        | `await Task.WhenAll` | `Task.WaitAll`               |
| Waiting for a period of time             | `await Task.Delay`   | `Thread.Sleep`               |

# Async Code & LINQ
Use caution.  LINQ uses deferred (lazy) execution, so async calls won't happen immediately (unless iteration is forced via `.ToList()` or `.ToArray()`)
