---
title: quantify
date: 2022-11-08T21:02:55-0700
draft: false
weight: 1
tags:
 - kb/dotnet/linq/standard-query-operators/quantifiers
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/linq/standard-query-operators/quantifier-operations)
A quantifying operation return Boolean for whether some or all of the elements in a set satisfy a condition.

# methods
| Method     | Description                                                   | Query expression |
| ---------- | ------------------------------------------------------------- | ---------------- |
| `All`      | Bool whether all elements in a collection satisfy a condition | N/A              |
| `Any`      | Bool whether any elements in a collection satisfy a condition | N/A              |
| `Contains` | Bool whether a collection contains a specified element        | N/A              |

# `All`
In this example, find students that scored above 70 on *all* exams:
```cs
IEnumerable<string> names = from student in students
                            where student.Scores.All(score => score > 70)
                            select $"{student.FirstName} {student.LastName}: {string.Join(", ", student.Scores.Select(s => s.ToString()))}";
```

# `Any`
In this example, find students that scored above 95 on *any* exam:
```cs
Enumerable<string> names = from student in students
                            where student.Scores.Any(score => score > 95)
                            select $"{student.FirstName} {student.LastName}: {student.Scores.Max()}";
```

# `Contains`
In this example, find students that scored exactly 95 on an exam:
```cs
IEnumerable<string> names = from student in students
                            where student.Scores.Contains(95)
                            select $"{student.FirstName} {student.LastName}: {string.Join(", ", student.Scores.Select(s => s.ToString()))}";
```