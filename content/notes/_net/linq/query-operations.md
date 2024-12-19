---
title: query operations
date: 2022-11-05T22:15:01-0600
draft: false
weight: 1
tags:
 - kb/dotnet/linq
---

# [Query Operations](https://learn.microsoft.com/en-us/dotnet/csharp/linq/get-started/walkthrough-writing-queries-linq)
LINQ queries can be filtered, sorted (ordered), grouped, joined, and selected.

For the following examples, consider a collection of this type:
```cs
public record Student(string First, string Last, int ID, int[] Scores);
```

# Filtering
The `where` clause is used to filter:

```cs
IEnumerable<Student> studentQuery =
    from student in students
    where student.Scores[0] > 90
    select student;
```

A more complex filter:
```cs
IEnumerable<Student> studentQuery =
    from student in students
    where student.Scores[0] > 90 && student.Scores[3] < 80
    select student;
```

# Sorting (Ordering)
The `orderby` clause is used to sort:

```cs
IEnumerable<Student> studentQuery =
    from student in students
    where student.Scores[0] > 90 && student.Scores[3] < 80
    orderby student.Last
    select student;
```

To default sort order is *ascending*. To reverse the sort order:
```cs
IEnumerable<Student> studentQuery =
    from student in students
    where student.Scores[0] > 90 && student.Scores[3] < 80
    orderby student.Last descending
    select student;
```

# Grouping
A query with a `group` clause produces a sequence of groups.  
Each group contains a `Key` and a sequence that contains all members of that group.

Example: grouping students by first letter of last name as the key:
```cs
IEnumerable<IGrouping<char, Student>> studentQuery =
    from student in students
    group student by student.Last[0];
```

Notice that the query variable, `studentQuery`, is of type `IGrouping<char, Student>`. This is because the
`group` clause produces a sequence of groups that have a `char` type as the key, and a sequence of `Student` objects.

To iterate over the query:
```cs
foreach (var studentGroup in studentQuery)
{
    Console.WriteLine(studentGroup.Key);

    foreach (var student in studentGroup)
    {
        Console.WriteLine($"{student.Last} {student.First}");
    }
}
```

## Sorting (ordering) by key value via `into` keyword
To sort the groups in the previous query, use an `orderby` clause after the `group` clause. To do this, you
need an identifier to reference the groups created by the `group` clause. You create this identifier with the
`into` keyword:

```cs
var studentQuery4 =
    from student in students
    group student by student.Last[0] into studentGroup
    orderby studentGroup.Key
    select studentGroup;

foreach (var groupOfStudents in studentQuery4)
{
    Console.WriteLine(groupOfStudents.Key);

    foreach (var student in groupOfStudents)
    {
        Console.WriteLine($"   {student.Last}, {student.First}");
    }
}
```

# Using `let` keyword to create ad hoc identifiers
The `let` clause can be used to create an identifier for any expression result in the query expression.

To find the students whose first test score was higher than their average of all test scores:
1. Use the `let` keyword to create an identifier, `avgScore`, that holds the average.
2. Use the `where` clause to filter only those cases where the first test score was higher than the average:

```cs
var studentQuery5 =
    from student in students
    let avgScore = (student.Scores[0] + student.Scores[1] +
                    student.Scores[2] + student.Scores[3]) / 4
    where student.Scores[0] > avgScore
    select $"{student.Last}, {student.First}";

foreach (string s in studentQuery5)
{
    Console.WriteLine(s);
}
```

# Transforming (Projecting)
Although this query is working with a sequence of `Student` objects, it returns a sequence of `string` objects:

```cs
IEnumerable<string> studentQuery =
    from student in students
    where student.Last == "Garcia"
    select student.First;
```

Assume that `averageClassScore` holds the value for the average test score of all students. To produce a query
that finds students whose average score is higher than the class average:
```cs
var aboveAverageQuery =
    from student in students
    let x = (student.Scores[0] + student.Scores[1] +
            student.Scores[2] + student.Scores[3]) / 4
    where x > averageScore
    select new { id = student.ID, score = x };

foreach (var item in aboveAverageQuery)
{
    Console.WriteLine("Student ID: {0}, Score: {1}", item.id, item.score);
} 