---
title: standard query operators
date: 2022-11-06T09:37:07-0700
draft: false
weight: 1
---

# overview
The standard query operators are extension methods of `IEnumerable<T>` or `IQueryable<T>`. They are the static methods of the `Enumerable` and `Queryable` classes.

# manner of execution
Standard Query Operator methods can execute in *immediate* or *deferred* manner.  
If deferred, in *streaming* or *non-streaming* forms.

## deferred queries
A deferred query fetches the updated data from the data source each time query results are iterated.
A deferred query can be forced to execute immediately with `Enumerable.ToList` or `Enumerable.ToArray`.

# query operators with equivalent query expression clauses

| Method       | Query expression                 | Notes                                       |
| ------------ | -------------------------------- | ------------------------------------------- |
| `Cast`       | `from int i in numbers`          | Requires an explicitly typed range variable |
| `GroupBy`    | `group … by`                     | group … by … into …                         |
| `GroupJoin`  | `join … in … on … equals … into` |
| `Join`       | `join … in … on … equals …`      |
| `OrderBy`    | `orderby`                        |
| `Select`     | `select`                         |
| `SelectMany` | multiple `from` clauses          |
| `ThenBy`     | `orderby …, …`                   |
| `Where`      | `where`                          |
