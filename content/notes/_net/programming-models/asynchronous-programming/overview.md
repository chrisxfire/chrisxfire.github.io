---
title: overview
date: 2022-02-16T00:00:00-06:00
draft: false
weight: -1
---

# Abstract
> Documentation: https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming/
> Documentation: https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming/async-scenarios#overview-of-the-asynchronous-model

Asynchronous programming allows for the execution of long-running operations that do not block the main thread. 

Concepts:
- *Synchronous* operations complete sequentially; the next task does not start until the previous finishes. 
- *Asynchronous* operations allow for starting a task then, while waiting for that task to finish, starting another.
- *Parallel* operations use multiple threads to execute several *asynchronous* tasks. They are *deterministic*: the order in which the tasks will complete is known.
- *Concurrent* operations use multiple threads to execute several *asynchronous* tasks. They are *nondeterministic*: the order in which the tasks will complete is not known.

.NET's asynchronous programming pattern described here is an implementation of the [promise model of asynchrony][promise-model] which uses the *futures* and *promises* constructs.

The asynchronous programming models uses `Task` and `Task<T>` objects which model asynchronous operations. Generally:
- For I/O-bound code, `await` a `Task` or `Task<T>` in a method marked `async`.
- For CPU-bound code, await an operation that is started on a background thread via `Task.Run`.

An example of I/O-bound code: downloading data from a web service:
```cs
private readonly HttpClient _httpClient = new HttpClient();

downloadButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI as the request from the web service is happening.
    //
    // The UI thread is now free to perform other work.
    var stringData = await _httpClient.GetStringAsync(URL);
    DoSomethingWithData(stringData);
};
```

An example of CPU-bound code: performing a calculation in a game:
```cs
private DamageResult CalculateDamageDone()
{
    // Code omitted: Performs an expensive calculation and returns the result of that calculation.
}

calculateButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI while CalculateDamageDone() performs its work. The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

## Asynchronous vs. Synchronous
Asynchronous code like `FryEggsAsync(2)` does not block:
```cs
// the async modifier signals that the method contains an await
static async Task Main() 
{ 
	Egg eggs = await FryEggsAsync(2);
	Console.WriteLine("eggs are ready");
}
```

Synchronous code will block the thread executing it from doing any other work.  It cannot be interrupted:
```cs
static void Main() 
{
	Egg eggs = FryEggs(2);
	Console.WriteLine("eggs are ready");
}
```

## Concurrent
Concurrent code like `Task<Egg> eggsTask = FryEggsAsync(2)` does not block and allows for concurrent execution:
```cs
static async Task Main() 
{
	Task<Egg> eggsTask = FryEggsAsync(2);
	Eggs eggs = await eggsTask;
	Console.WriteLine("eggs are ready");
}
```

## Composition
If any portion of an operation is asynchronous, the entire operation is asynchronous.  
The composition of an asynchronous operation followed by synchronous work is asynchronous:
```cs
static async Task<Toast> MakeToastWithButterAndJamAsync() 
{
	var toast = await ToastBreadAsync();	// the asynchronous operation
	ApplyButter(toast);				// the synchronous operations
	ApplyJam(toast);
	
	return toast;
}
```

# Async


# Async Code & LINQ
Use caution.  LINQ uses deferred (lazy) execution, so async calls won't happen immediately (unless iteration is forced via `.ToList()` or `.ToArray()`)

# Expression-Bodied Methods
If a method is expression-bodied, it can omit the async and await keywords:

```cs
static Task Main() => DoSomethingAsync();
```
…is equivalent to:
```cs
static async Task Main() 
{
	await DoSomethingAsync();
}
```

# Other .NET Asynchronous Programming Patterns
These notes describe the Task Asynchronous Pattern, which is covered in more detail in the notes linked below.

| Model                                                               | Abbr | Language <br /> constructs                                | Notes                                                                                                                                     |
| ------------------------------------------------------------------- | ---- | --------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Task Asynchronous Pattern <br /> Modern, easier to use              | TAP  | `async`/`await`                                           | [Notes on TAP](../../asynchronous-programming/task-asynchronous-programming/overview)                                                        |
| Asynchronous Programming Model <br /> Legacy, more difficult to use | APM  | `IAsyncResult`, `Begin`, `End`                            | [Notes on APM](../../asynchronous-programming/asynchronous-programming-model/overview) <br /> Legacy pattern; not recommended for new development |
| Event-based Asynchronous Pattern                                    | EAP  | Events, event-handler delegates, `EventArg`-derived types | Legacy pattern; not recommended for new development                                                                                       |

.NET also has a parallel programming pattern: the Task Parallel Library ([Notes on TPL](../../parallel-programming/)).

[promise-model]: https://en.wikipedia.org/wiki/Futures_and_promises