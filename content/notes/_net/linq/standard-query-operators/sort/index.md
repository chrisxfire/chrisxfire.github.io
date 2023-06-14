---
title: notes > .net > linq > standard query operators > sort
date: 2022-11-07T21:31:15-0700
draft: false
---
A sorting operation orders the elements of a sequence based on one or more attributes.

# Methods
| Method | Description                             | Query expression |
|------------|---------------------------------------------|----------------------|
| `OrderBy`    | Sort values in ascending order              | `orderby`              |
| `ThenBy`     | Perform a secondary sort in ascending order | `orderby …, …`         |
| `Reverse`    | Reverse the order of the elements           | N/A                  |

# Query Expression
## Sort Ascending
```cs
string[] words = { "the", "quick", "brown", "fox", "jumped", "over", "the", "lazy", "dog" };

var query = from word in words
    orderby word.Length
    select word;
```

## Sort Secondary Ascending
```cs
var query = from word in words
    order by word.Length, // First, sort by length
    word.Substring(0, 1) // then by the first letter of the word
    select word;
```
