---
title: notes > code > .net > programming models > asynchronous programming > streams
date: 2022-11-23T10:22:25-0700
draft: false
weight: 1
---
# Async Streams
An async method may return an async stream via `IAsyncEnumerable<T>`.
Use this to enumerate items read from a stream when elements are generated in chunks via repeated async calls.

# Creating
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
# Consuming
Async streams are consumed via an await foreach statement:
```cs
await foreach (var word in ReadWordsFromStreamAsync())
{
    …
}
```

`IAsyncEnumerator<T>` derives from `IAsyncDisposable.` It is automatically disposed after a foreach loop.
