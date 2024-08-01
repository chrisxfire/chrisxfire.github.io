---
title: async
date: 2023-10-07T00:00:00-06:00
draft: false
weight: 1
---

# Overview [[Documentation](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/async)]  

The `async` modifier specifies that a method, lambda, or anonymous method is *asynchronous*. 
- An async method runs synchronously until it reaches an `await` expression. At this point, the method is suspended
until the awaited task is complete. In the meantime, control returns to the caller of the async method.
- An async method does not run on their own thread by default.

Behind the scenes, the the C# compiler transforms the method into a state machine. If an async method does not have
an `await` expression in its body, it never yields, which wastes the expensive state machine. In such a case, the 
entire method runs synchronously.

Do not use `out` and `ref` parameters in async methods. Instead, return data that would have been returned through `out`/`ref` in the `TResult` of `Task<TResult>`. 
Use a tuple or custom type to accommodate multiple return values.

# Async Return Types [[Documentation](https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming/async-return-types)]  

Async methods can return:
- `Task` — async methods that performs an operation but return no value (like `void` synchronous methods)
- `Task<T>` — async methods that return a value
- `void` — for asynchronous event handlers
- `IAsyncEnumerable<T>` — async methods that return an *async stream*
- Any type that has an accessible `GetAwaiter` method (must implement `System.Runtime.CompilerServices.ICriticalNotifyCompletion`)

## Void Return Type
An async void method is used only for event handlers (because event handlers do not have a return type):
- Such a method cannot be awaited.
- The caller of such a method cannot catch exceptions that the method throws.

## `IAsyncEnumerable<T>` (Async Streams) [[Documentation](https://learn.microsoft.com/en-us/dotnet/csharp/asynchronous-programming/async-return-types#async-streams-with-iasyncenumerablet)]  

An async method may return an async stream via `IAsyncEnumerable<T>`.
Use this to enumerate items read from a stream when elements are generated in chunks via repeated async calls.

### Creating
```cs
static async IAsyncEnumerable<string> ReadWordsFromStreamAsync()
{
    string data =
    @"This is a line of text.
    Here is the second line of text.
    And there is one more for good measure.
    Wait, that was the penultimate line.";

    using var readStream = new StringReader(data);

    string? line = await readStream.ReadLineAsync(); // Read a line
    while (line != null)
    {
        foreach (string word in line.Split(' ', StringSplitOptions.RemoveEmptyEntries))
        yield return word; // Enumerate each word in the line

        line = await readStream.ReadLineAsync();
    }
}
```
### Consuming
Async streams are consumed via an await foreach statement:
```cs
await foreach (var word in ReadWordsFromStreamAsync())
{
    …
}
```

`IAsyncEnumerator<T>` derives from `IAsyncDisposable.` It is automatically disposed after a foreach loop.