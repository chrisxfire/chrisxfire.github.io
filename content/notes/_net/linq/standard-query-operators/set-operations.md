---
title: set operations
date: 2022-11-08T20:37:38-0700
draft: false
weight: 1
tags:
 - kb/dotnet/linq/standard-query-operators/set-operations
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/linq/standard-query-operators/set-operations)
Set operations are query operations that produce a result set that is based on the presence or absence of 
equivalent elements within the same or separate sets.

# methods
| Method          | Description                                                            | Query expression |
| --------------- | ---------------------------------------------------------------------- | ---------------- |
| `Distinct(By)`  | Removes duplicate values from a collection                             | N/A              |
| `Except(By)`    | Returns the elements of one collection that do not appear in the other | N/A              |
| `Intersect(By)` | Elements that appear in each of two collections                        | N/A              |
| `Union(By)`     | Unique elements that appear in either of two collections               | N/A              |

The `*By` methods take a `keySelector` which is used as the comparative discriminator of the source type.

# `Distinct` and `DistinctBy`
These methods both take a single collection.

`Distinct` returns the unique elements in a collection:

```cs
string[] words = ["the", "quick", "brown", "fox", "jumped", "over", "the", "lazy", "dog"];

IEnumerable<string> query = from word in words.Distinct()
                            select word;
```

`DistinctBy`, like all `*By` methods, takes a `keySelector` which is used as the comparative discriminator of the source type.

In this example, the first word of each length is displayed:
```cs
foreach (string word in words.DistinctBy(p => p.Length))
    Console.WriteLine(word);
```

# `Except` and `ExceptBy`
These methods both take two collections.

`Except` returns only the elements from the first collection that are not present in the second:

```cs
string[] words1 = ["the", "quick", "brown", "fox"];
string[] words2 = ["jumped", "over", "the", "lazy", "dog"];

IEnumerable<string> query = from word in words1.Except(words2)
                            select word;
```

`ExceptBy`'s `keySelector` is of the same type as the first collection's type.

To find teachers in the first collection that are not in the second collection, project the teacher's ID onto the
second collection:
```cs
int[] teachersToExclude =
[
    901,    // English
    965,    // Mathematics
    932,    // Engineering
    945,    // Economics
    987,    // Physics
    901     // Chemistry
];

foreach (Teacher teacher in teachers.ExceptBy(teachersToExclude, teacher => teacher.ID))
    Console.WriteLine($"{teacher.First} {teacher.Last}");
```

# `Intersect` and `IntersectBy`
These methods both take two collections.

`Intersect` returns a collection of elements that are common to both input collections:
```cs
string[] words1 = ["the", "quick", "brown", "fox"];
string[] words2 = ["jumped", "over", "the", "lazy", "dog"];

IEnumerable<string> query = from word in words1.Intersect(words2)
                            select word;
```

`IntersectBy`'s `keySelector` is used as the comparative discriminator of the second collection's type:
```cs
foreach (Student person in students.IntersectBy(
        teachers.Select(t => (t.First, t.Last)), s => (s.FirstName, s.LastName)))
{
    Console.WriteLine($"{person.FirstName} {person.LastName}");
}
```

# `Union` and `UnionBy`
These methods both take two collections.

`Union` returns a collection that contains the unique elements from both input collections:
```cs
string[] words1 = ["the", "quick", "brown", "fox"];
string[] words2 = ["jumped", "over", "the", "lazy", "dog"];

IEnumerable<string> query = from word in words1.Union(words2)
                            select word;
```

`UnionBy`'s `keySelector` is used as the comparative discriminator of the source collection's type:
```cs
foreach (var person in
    students.Select(s => (s.FirstName, s.LastName)).UnionBy(
        teachers.Select(t => (FirstName: t.First, LastName: t.Last)), s => (s.FirstName, s.LastName)))
{
    Console.WriteLine($"{person.FirstName} {person.LastName}");
}
```