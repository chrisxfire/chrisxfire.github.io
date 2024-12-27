---
title: sort
date: 2022-11-07T21:31:15-0700
draft: false
weight: 1
tags:
 - kb/dotnet/linq/standard-query-operators/sort
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/linq/standard-query-operators/sorting-data)
A sorting operation orders the elements of a sequence based on one or more attributes.

# Methods
| Method                | Description                                              | Query expression                             |
| --------------------- | -------------------------------------------------------- | -------------------------------------------- |
| `OrderBy(Descending)` | Sort values in ascending (descending) order              | `orderby …` and `orderby … descending`       |
| `ThenBy(Descending)`  | Perform a secondary sort in ascending (descending) order | `orderby …, …` and `orderby …, … descending` |
| `Reverse`             | Reverse the order of the elements                        | N/A                                          |

# Primary Ascending Sort
```cs
string[] words = { "the", "quick", "brown", "fox", "jumped", "over", "the", "lazy", "dog" };
```

In query syntax:
```cs
var query = from word in words
            orderby word.Length
            select word;
```

In method syntax:
```cs
var query = words.OrderBy(w => w).Select(x => x);
```

# Secondary Sort Ascending
In query syntax:
```cs
var query = from word in words
    orderby word.Length, // First, sort by length
            word.Substring(0, 1) // then by the first letter of the word
    select word;
```

In method syntax:
```cs
var query = words.OrderBy(w => w.Length).ThenBy(x => x).Select(y => y);
```