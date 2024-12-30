---
title: group
date: 2022-11-10T20:15:40-0700
draft: false
weight: 1
tags:
 - kb/dotnet/linq/standard-query-operators/group
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/linq/standard-query-operators/grouping-data)
A group operation puts data into groups such that the elements in each group share a common attribute.

# methods
| Method     | Description                                                                                                           | Query expression |
| ---------- | --------------------------------------------------------------------------------------------------------------------- | ---------------- |
| `GroupBy`  | Groups elements that share a common attribute. Groups are represented by an `IGrouping<TKey,TElement>`.               | group … by       |
| `ToLookup` | Inserts elements into a `Lookup<TKey, TElement>` via a key-selector function. A `Lookup` is a one-to-many dictionary. | N/A              |

# `GroupBy` Example
Group integers into a list based on whether they are even or odd:
```cs
List<int> numbers = [35, 44, 200, 84, 3987, 4, 199, 329, 446, 208];

IEnumerable<IGrouping<int, int>> query = from number in numbers
                                         group number by number % 2;

foreach (var group in query)
{
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");
    foreach (int i in group)
    {
        Console.WriteLine(i);
    }
}
```

In method syntax:
```cs
List<int> numbers = [35, 44, 200, 84, 3987, 4, 199, 329, 446, 208];

IEnumerable<IGrouping<int, int>> query = numbers.GroupBy(number => number % 2);

foreach (var group in query)
{
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");
    foreach (int i in group)
    {
        Console.WriteLine(i);
    }
}
```

# more examples
Data can be grouped by:
1. A single property
2. The first letter of a string property
3. A computed numeric range
4. Boolean predicate or other expression
5. A compound key

See https://learn.microsoft.com/en-us/dotnet/csharp/linq/standard-query-operators/grouping-data#group-query-results.