---
title: notes > .net > linq > plinq
date: 2022-05-09T19:48:01-0600
draft: false
---
# [PLINQ](https://docs.microsoft.com/en-us/dotnet/standard/parallel-programming/introduction-to-plinq)
Parallel LINQ. Enable multiple threads to execute a query.
```cs
// Single-threaded:
int[] fibonacciNumbers = numbers
    .Select(number => Fibonacci(number))
    .ToArray();

// Multi-threaded:
int[] fibonacciNumbers = numbers
    .AsParallel()
    .Select(number => Fibonacci(number))
    .OrderBy(number => number) // Parallel execution can cause results to become disordered.
    .ToArray();
```
