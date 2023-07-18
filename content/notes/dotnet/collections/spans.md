---
title: notes > .net > collections > spans
date: 2022-01-09T18:14:15-0700
draft: false
weight: 1
---
# Spans
Spans are a window into the original array. Spans only work with arrays.
Spans uses `Index` and `Range` types.
```cs
string name = "Samantha Jones";

int lengthOfFirst = name.indexOf(' '); // The length of the first name.
int lengthOfLast = name.Length - lengthofFirst - 1; // The length of the last name.

ReadOnlySpan<char> nameAsSpan = name.AsSpan(); // Convert the string to a span.
ReadOnlySpan<char> firstNameSpan = nameAsSpan[0..lengthOfFirst];
ReadOnlySpan<char> lastNameSpan = nameAsSpan[^lengthOfLast..^0];

Console.WriteLine($"First name: {firstNameSpan.ToString()}, Last name: {lastNameSpan.ToString());
```
