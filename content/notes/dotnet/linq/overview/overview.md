---
title: notes > .net > linq > overview > overview
date: 2022-04-20T10:06:47-0600
draft: false
weight: -1
---
# Overview
LINQ (Language-Integrated Query) is a set of technologies that integrates query capabilities directly into C#.

## <u>Architecture</u>
LINQ consists of:
- *Extensions methods* (required) – `Where`, `OrderBy`, `Select`, etc
- *LINQ providers* (required) – LINQ to Objects, LINQ to Entities, LINQ to XML, LINQ to SQL
- *Lambda expressions* (optional) – can be used instead of named methods.
- *LINQ query syntax* (optional) – `from`, `in`, `where`, `orderby`, etc.

## Queryable Types
Queryable types are those types that can be queried via LINQ. They are the set of all types that implement IEnumerable<T> or a derivative.

# Query Syntax vs. Method Syntax
- All query expressions are converted to Standard Query Operator method calls at compile time.
- Any query that can be expressed in *query syntax* can also be expressed using *method syntax*.
  - Use query syntax whenever possible, method syntax whenever necessary.
    - There is no performance difference between the two.
- Some query operations like Count or Max have no query syntax equivalent and require method syntax.
- Method syntax can be combined with query syntax.

## Query Syntax Example
```cs
// Obtain the data source:
int[] scores = { 97, 92, 81, 60 };

// Create the query:
IEnumerable<int> scoreQuery = // `scoreQuery` is the *query variable*
  // `score` is the *range variable;* it is in scope until query is exited with a semicolon
  from score in scores // `scores` is the *data source*
  where score > 80// this is the *filter*
  select score;

// Execute the query.
foreach (int i in scoreQuery) // The *iteration variable* (i) iterates over the query variable (scoreQuery), thereby
  Console.Write(i + " "); // executing it.
// Output: 97 92 81
```

## Method Syntax Example
```cs
// The same query in method syntax:
IEnumerable<int> scoreQuery = scores.Where(score => score > 80);
```

## Mixed Query and Method Syntax
When mixing the two syntaxes, instead of this:
```cs
int numCount1 = (
  from num in numbers1
  where num < 3 || num > 7
  select num).Count();
```

Do this (create a new variable to store the method call result):
```cs
IEnumerable<int> numbersQuery =
  from num in numbers1
  where num < 3 || num > 7
  select num;

int numCount2 = numbersQuery.Count(); // This method call forces the query expression to execute immediately.
```

# Query Use Cases
## 1
```cs
IEnumerable<int> highScoresQuery =
  from score in scores
  where score > 80 // Get a subset of the data…
  orderby score descending // …then sort/group it.
  select score;
```

## 2 
```cs
IEnumerable<string> highScoresQuery2 =
  from score in scores
  where score > 80 // Get a subset of the data…
  orderby score descending
  select $"The score is {score}"; // …then transform it (int –> string).
```

## 3 
```cs 
int highScoreCount = ( // Because highScoreCount stores a result, it is *not* a query variable.
  from score in scores
  where score > 80 // Get a subset of the data…
  select score).Count(); // …then get a singleton value about the data.
```
