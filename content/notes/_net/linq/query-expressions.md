---
title: query expressions
date: 2024-12-15T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/dotnet/linq
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/linq/get-started/query-expression-basics)
A *query expression* is a query expressed in *query syntax*. All query expressions are converted to Standard Query Operator method calls at compile time.

Query expressions:
- Must begin with a `from` clause
- Optionally contain `where`, `orderby`, `join`, `let,` or other `from` clauses
- Must end with a `select` or `group` clause
 
# query syntax
Query syntax looks like this:
```cs
int[] numbers = [ 5, 10, 8, 3, 6, 12 ];

IEnumerable<int> numQuery1 = // 'numQuery1' is the query variable
    from num in numbers // 'num' is the range variable; it is typed based on the type of elements in 'numbers'
    where num % 2 == 0
    orderby num
    select num;

foreach (int i in numQuery1) // The iteration variable (i) iterates over the query variable (numQuery1), thereby executing it
{
    Console.Write(i + " ");
}
```

Any query that can be expressed in *query syntax* can also be expressed using *method syntax*.
- Use query syntax whenever possible, method syntax whenever necessary. There is no performance difference between the two.
- Some query operations like `Count` or `Max` have no query syntax equivalent and require method syntax.
- Method syntax can be combined with query syntax.

# method syntax
Method syntax is made possible by extension methods on `IEnumerable<T>` (and `IQueryable<T>`) that implement the standard query operators.

Method syntax looks like this:
```cs
IEnumerable<int> numQuery2 = numbers.Where(num => num % 2 == 0)
                                    .OrderBy(n => n);
```

The `Where` extension method implements the `where` standard query operator.  
The `OrderBy` extension method implements the `orderby` standard query operator.

> [!NOTE]
> Some LINQ providers implement their own standard query operators and extension methods for types other than `IEnumerable<T>`.

## mixed query and method syntax
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

# subqueries
When a query clause contains a query expression, this is called a *subquery*. Each subquery starts with its own
`from` clause. These are common when retrieving the results of a grouping operation:

```cs
var queryGroupMax =
    from student in students
    group student by student.Year into studentGroup
    select new
    {
        Level = studentGroup.Key,
        HighestScore = (
            from student2 in studentGroup
            select student2.ExamScores.Average()
        ).Max()
    };
```

# query use cases
## filter the data
```cs
IEnumerable<int> filteringQuery =
    from score in scores
    where score > 80 or < 90
    select score;
```

## Sort/group a subset of the data
```cs
IEnumerable<int> highScoresQuery =
    from score in scores
    where score > 80 // Get a subset of the data…
    orderby score descending // …then sort/group it.
    select score;
```

## transform a subset of the data
```cs
IEnumerable<string> highScoresQuery2 =
    from score in scores
    where score > 80 // Get a subset of the data…
    orderby score descending
    select $"The score is {score}"; // …then transform it (int –> string).
```

## get a singleton value about the data
```cs 
int highScoreCount = ( // Because highScoreCount stores a result, it is *not* a query variable.
    from score in scores
    where score > 80 // Get a subset of the data…
    select score).Count(); // …then get a singleton value about the data.
``` 

# Handle `null` in query expressions
If a source collection is `null` or contains an element whose value is `null`, and the query expression
does not guard against these cases, a `NullReferenceException` is thrown when the query is executed.

To guard:
```cs
if (categories is not null) // explicitly check the source collection for null
{
    var query1 =
        from c in categories
        where c != null // where clause filters out null elements in the 'categories' sequence
        join p in products on c.ID equals p?.CategoryID
        select new
        {
            Category = c.Name,
            Name = p.Name
        };
}
```