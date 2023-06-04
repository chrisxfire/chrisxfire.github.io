---
title: "notes > dotnet > linq > standard query operators > filter"
date: 2022-11-08T20:55:04-0700
draft: false
---
A filtering operation restricts the result set to contain only those elements that satisfy a specified condition.

Methods
| Method | Description                                                                | Query expression |
|--------|----------------------------------------------------------------------------|------------------|
| `OfType` | Selects values depending on their ability to be cast to the specified type | N/A              |
| `Where ` | Selects values based on a predicate function                               | N/A              |

Example
```cs
string[] words = { "the", "quick", "brown", "fox", "jumps" };

words.Where(w => w.Length == 3);
```