---
title: filter
date: 2022-11-08T20:55:04-0700
draft: false
weight: 1
tags:
 - kb/dotnet/linq/standard-query-operators/filter
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/linq/standard-query-operators/filtering-data)
A filtering operation restricts the result set to contain only those elements that satisfy a specified condition. The
condition is called a *predicate*. 

# methods
| Method   | Description                                                                | Query expression |
| -------- | -------------------------------------------------------------------------- | ---------------- |
| `OfType` | Selects values depending on their ability to be cast to the specified type | N/A              |
| `Where ` | Selects values based on a predicate function                               | `where`          |

# example
```cs
string[] words = [ "the", "quick", "brown", "fox", "jumps" ];
```

In method syntax:
```cs
IEnumerable<string> query =
    words.Where(word => word.Length == 3);
```

In query syntax:
```cs
IEnumerable<string> query = from word in words
                            where word.Length == 3
                            select word;

```
