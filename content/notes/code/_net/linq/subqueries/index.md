---
title: notes > code > .net > linq > subqueries
date: 2022-04-27T18:56:35-0600
draft: false
weight: 1
---
# Subqueries
A query clause may itself contain a query expression (a subquery).
Each subquery starts with its own `from` clause that does not necessarily point to the same data source as the first `from` clause.

```cs
var queryGroupMax = 
    from student in students // for each student in the `students` sequence…
    group student by student.Year into studentGroup // …group the student by `.Year` into new variable `studentGroup`.
    select new
    {
        Level = studentGroup.Key, // (what does Level have to do with this?)
        HighestScore = ( // This is the subquery.
            from student2 in studentGroup
                select student2.ExamScores.Average()
            ).Max()
    };
```
