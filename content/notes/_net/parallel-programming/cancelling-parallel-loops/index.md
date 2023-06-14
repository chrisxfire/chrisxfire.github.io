---
title: notes > .net > parallel programming > cancelling parallel loops
date: 2023-02-16T15:23:54-0700
draft: false
---
# Overview
Cancellation is achieved by:
1.  Supplying a `CancellationToken` to the `Parallel.For` or `Parallel.ForEach` method's `ParallelOptions` parameter
2.  Enclosing the parallel call in a `try-catch` block

Example
```cs
int[] nums = Enumerable.Range(0, 1_000_000).ToArray();

using CancellationTokenSource cts = new();

ParallelOptions po = new();
po.CancellationToken = cts.Token;

try
{
    Parallel.ForEach(nums, po, (num) =>
    {
    double d = Math.Sqrt(num);
    Console.WriteLine($"{d} on {Thread.CurrentThread.ManagedThreadId}");
    });
}
catch
{
    …
}
```
