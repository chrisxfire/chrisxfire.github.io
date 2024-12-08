---
title: with expressions
date: 2024-11-07T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/dotnet/fundamentals/expressions/with
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/with-expression)
`with` expressions are used to create new objects that are modified copies of existing ones (non-destructive mutation).
The left-hand operand can be a record, struct, or anonymous type:
```cs
public record NamedPoint(string Name, int X, int Y);

public static void Main()
{
    var p1 = new NamedPoint("A", 0, 0);
    Console.WriteLine($"{nameof(p1)}: {p1}");  // output: NamedPoint { Name = A, X = 0, Y = 0 }
    
    var p2 = p1 with { Name = "B", X = 5 };    // output: NamedPoint { Name = B, X = 5, Y = 0 }
    
    var p3 = p1 with 
        { 
            Name = "C", 
            Y = 4 
        };                                     // output: NamedPoint { Name = C, X = 0, Y = 4 }
}
```