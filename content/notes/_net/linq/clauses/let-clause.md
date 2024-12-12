---
title: let clause
date: 2022-04-27T18:53:40-0600
draft: false
weight: 1
---

# Let clause
Use the let clause to store the result of an expression, such as a method call, in a new range variable (identifier).

## Example 1
```cs
var studentQuery = from student in students
    let totalScore = studentScores[0] + student.Scores[1] +
        studentScores[2] + student.Scores[3]
    select totalScore; // The new identifer can also be selected
```

## Example 2
```cs
var studentQuery =
    from student in students
    let x = student.Scores[0] + student.Scores[1] +
        student.Scores[2] + student.Scores[3]
    where x > averageScore
    select new { id = student.ID, score = x }; // A new anonymous type of a sequence of Students with their score and student ID
```

