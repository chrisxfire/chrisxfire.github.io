---
title: overview
date: 2022-02-16T16:22:37-0700
draft: false
weight: -1
---

# classes
A reference type that encapsulates behavior.

## characteristics
- Allocation: Heap
- Equality: Reference
- Semantics: Reference (a variable of a class contains a reference to that class)
- Inheritance: Single
- Mutability: Mutable

## use when
- You need to describe behavior and not just data

# creating classes
Note: When creating custom classes, always override ToString() to provide information about the type (not shown here).
```cs
public class Point
{
    private int _X { get; } // Auto-implemented readonly property.
    private int _Y { get; }

    // Constructor that takes 0 arguments:
    public Point() => (0, 0);

    // Constructor that takes 2 arguments:
    public Point(int x, int y) => (_X, _Y) = (x, y);
    // This constructor also ensures that _X and _Y are set so that they cannot be null, avoiding null reference.

    // Another example that uses the "this" keyword to refer to members of the instance:
    public Point(int x, int y) 
    {
        this._X = x;
        this._Y = y;
    }

    // A method that overrides the base class (System.Object) implementation of ToString():
    public override string ToString() => return $"({X}, {Y})"
}
```

## Creating Objects (Instantiating a Class)
```cs
var p = new Point(x: *n*, y: *m*) // Constructor syntax.
p = new Point { x = *n*, y = *m* } // Initializer syntax.
Point p = new() { x = n, y = m }
```

# equality
`Object.Equals` Boolean if two reference-type objects refer to the same location in memory.
