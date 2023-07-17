---
title: notes > .net > linq > standard query operators > generate
date: 2022-11-10T20:42:58-0700
draft: false
weight: 1
---
A generate operation creates a new sequence of values.

# Methods
| Method         | Description                                                            | Query expression |
|----------------|------------------------------------------------------------------------|------------------|
| `DefaultIfEmpty` | Replace an empty collection with a default-valued singleton collection | N/A              |
| `Empty`          | Return an empty collection                                             | N/A              |
| `Range`          | Generate a collection that contains a sequence of numbers              | N/A              |
| `Repeat`         | Generate a collection that contains one value repeated n times         | N/A              |

# Examples
```cs
IEnumerable<int> squares = Enumerable.Range(1, 10).Select(x => x * x);

squares.ForEach(i => Console.WriteLine(i)); // Output: 1 4 9 16 25 36 49 64 81 100
```
