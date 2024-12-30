---
title: convert
date: 2022-11-13T18:58:51-0700
draft: false
weight: 1
tags:
 - kb/dotnet/linq/standard-query-operators/converters
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/linq/standard-query-operators/converting-data-types)
Convert methods change the type of objects.

# methods
`As*` methods change the static type of the collection but do not enumerate it.  
`To*` methods enumerate the collection and put the items into a different collection type.

Methods marked with * force query execution:

| Methods         | Description                                                                      | Query expression           |
| --------------- | -------------------------------------------------------------------------------- | -------------------------- |
| `AsEnumerable`  | Returns the input typed as `IEnumerable<T>`                                      | N/A                        |
| `AsQueryable`   | Converts an `IEnumerable` to `IQueryable`                                        | N/A                        |
| `Cast<T>`       | Casts the elements of a collection to type `T`                                   | `from <type> var in words` |
| `OfType`        | Selects values depending on their ability to be cast to the specified type       | N/A                        |
| *`ToArray`      | Converts a collection to an array                                                | N/A                        |
| *`ToDictionary` | Puts elements into a `Dictionary<TKey, TValue>` based on a key-selector function | N/A                        |
| *`ToList`       | Converts a collection to a `List<T>`                                             | N/A                        |
| *`ToLookup`     | Puts elements into a `Lookup<TKey, TValue>` based on a key-selector function     | N/A                        |

# `Cast<T>` example
In this example, cast a type to a subtype:
```cs
IEnumerable people = students;

var query = people
    .Cast<Student>()
    .Where(student => student.Year == GradeLevel.ThirdYear);
```