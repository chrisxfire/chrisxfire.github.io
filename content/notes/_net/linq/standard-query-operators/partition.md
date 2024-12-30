---
title: partition
date: 2022-11-08T21:36:23-0700
draft: false
weight: 1
tags:
 - kb/dotnet/linq/standard-query-operators/partitioners
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/linq/standard-query-operators/partitioning-data)
A partitioning operation divides an input set into two sections, without rearranging the elements, and then returning one of the sections.

Partitioning operations have no query syntax.

# methods
| Method      | Description                                                                                  |
| ----------- | -------------------------------------------------------------------------------------------- |
| `Skip`      | Skips elements up to a specified position in the collection                                  |
| `SkipWhile` | Skips elements based on a predicate function until an element does not satisfy the condition |
| `Take`      | Takes elements up to a specified position in a collection                                    |
| `TakeWhile` | Takes elements based on a predicate function until an element does not satisfy the condition |
| `Chunk`     | Splits elements of a collection into chunks of a specified maximum size                      |

# examples
Assume some sequence: `0 1 2 3 4 5 6 7`
- `Take(3)` returns `0 1 2`
- `Skip(3)` returns `3 4 5 6 7`
- `TakeWhile(n => n < 5)` returns `0 1 2 3 4`
- `SkipWhile(n => n < 5)` returns `5 6 7`
- `Chunk(3)` returns `[0, 1, 2], [3, 4 5], [6, 7]`