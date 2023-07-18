---
title: "notes > .net > toolkits > communitytoolkit.diagnostics"
date: 2023-02-28T15:58:54-0700
draft: false
weight: 1
---
# Overview
APIs to validate parameters and throw exceptions in faulting code paths.

```powershell
dotnet add package CommunityToolkit.Diagnostics
```

```cs
using CommunityToolkit.Diagnostics;
```

# `Guard`
Helper methods that verify conditions when code is running and throw exceptions in one line.  
Contains methods for comparisons, strings, collections, and tasks.

Engineering Note 2023-03-02: `Guard.IsNullOrEmpty` is not considered a null check by the C# analyzer and so even types with this guard will still report as maybe-null.

## Without `Guard`
```cs
public static void SampleMethod(int[] array, int index, Span<int> span, string text)
{
    if (array is null)
        throw new ArgumentNullException(nameof(array), "The array must not be null");

    if (array.Length >= 10)
        throw new ArgumentException($"The array must have less than 10 items, had a size of {array.Length}", nameof(array));

    if (index < 0 || index >= array.Length)
        throw new ArgumentOutOfRangeException(nameof(index), $"The index must be in the [0, {array.Length}) range, was {index}");

    if (span.Length < array.Length)
        throw new ArgumentException($"The target span is shorter than the input array, had a length of {span.Length}", nameof(span));

    if (string.IsNullOrEmpty(text))
        throw new ArgumentException("The input text can't be null or empty", nameof(text));
}
```

## With `Guard`
```cs
public static void SampleMethod(int[] array, int index, Span<int> span, string text)
{
    Guard.IsNotNull(array);
    Guard.HasSizeGreaterThanOrEqualTo(array, 10);
    Guard.IsInRangeFor(index, array);
    Guard.HasSizeLessThanOrEqualTo(array, span);
    Guard.IsNotNullOrEmpty(text);
}
```

# `ThrowHelper`
Used to efficiently throw exceptions. Complements `Guard`.  
Check if a `Guard` method exists first, and if not, use `ThrowHelper`.

```cs
// Replace this...
throw new InvalidOperationException("Some custom message from my library");

// ...with this:
ThrowHelper.ThrowInvalidOperationException("Some custom message from my library");
```
