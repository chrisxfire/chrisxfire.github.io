---
title: overview
date: 2024-12-18T00:00:00-06:00
draft: false
weight: -1
tags:
 - kb/dotnet/linq/standard-query-operators
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/linq/standard-query-operators/)
The *standard query operators* are keywords and methods that form the LINQ pattern. In method syntax, most of these
methods operate on sequences (an object whose type implements `IEnumerable<T>` or `IQueryable<T>`). The methods that
make up the standard query operators are static members of the `Enumerable` and `Queryable` classes implemented as
extension methods.  

There is a distinction between the `IEnumerable<T>` and `IQueryable<T>` sequences that determine how the query is
executed at runtime:
- For `IEnumerable<T>`, the returned object captures the arguments that were passed to the method. When *that* object
is enumerated, the logic of the query operator is employed, and the query results are returned.
- For `IQueryable<T>`, the query is first translated into an *expression tree*. An expression tree can be further
translated into a native query where the data source can optimize the query. Entity Framework, for example, translates
LINQ queries into native SQL queries that execute at the database.

The examples in these notes use collections of the following types:
```cs
public enum GradeLevel { FirstYear = 1, SecondYear, ThirdYear, FourthYear };

public record Student(string FirstName, string LastName, int ID, GradeLevel Year, List<int> Scores, int DepartmentID);

public record Teacher(string First, string Last, int ID, string City);

public record Department(string Name, int ID, int TeacherID);
```

> [!TIP]
> These notes do not cover all of the query method supported by the .NET runtime.  
> See documentation for [System.Linq.Enumerable](https://learn.microsoft.com/en-us/dotnet/api/system.linq.enumerable).

# operations
You can perform many operations with the standard query operators:
- Filter data using the `where` keyword.
- Order data using the `orderby` and optionally `descending` keywords.
- Group data using the `group` and optionally `into` keywords.
- Join data using the `join` keyword.
- Project data using the `select` keyword.

# query operators and their equivalent query expression clauses
| Method              | Query expression syntax                                        |
| ------------------- | -------------------------------------------------------------- |
| `Cast`              | Use an explicitly-typed range variable: `for int i in numbers` |
| `GroupBy`           | `group ... by ...` or `group ... by ... into ...`              |
| `GroupJoin`         | `join ... in ... on ... equals ... into ...`                   |
| `Join`              | `join ... in ... on ... equals ...`                            |
| `OrderBy`           | `orderby`                                                      |
| `OrderByDescending` | `orderby ... descending`                                       |
| `Select`            | `select`                                                       |
| `SelectMany`        | Multiple `from` clauses                                        |
| `ThenBy`            | `orderby ..., ...`                                             |
| `ThenByDescending`  | `orderby ..., ... descending`                                  |
| `Where`             | `where`                                                        |