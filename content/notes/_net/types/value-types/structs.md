---
title: structs
date: 2021-11-05T21:23:37-0600
draft: false
weight: 1
---

# [Structs](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/struct)
A value type that encapsulates data and related functionality.

## characteristics
- Allocation: *Stack*
- Equality: *Value* (albeit inefficient)
- Semantics: *Value* (a variable of a struct type contains an instance of that type)
- Inheritance: *None* (sealed)
- Mutability: *Mutable* (but, recommended to be made immutable with `readonly` modifier)

## use when
- You need a small, data-centric type with little or no behavior
- You need a type whose fields are only value types
- The total bytes used by all the fields in the type is 16 bytes or less
- .NET uses structs for numbers, booleans, unicode chars, time

# creating
Note: When creating custom structs, always override ToString() to provide information about the type (not shown here).

```cs
public struct Point 
{
    public double X { get; }
    public double Y { get; }
    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

## initialization
As of C#11, uninitialized fields are assigned their default value.

If all instance fields of a struct are accessible, the struct can be instantiated without the `new` operator.

## creating objects
```cs
Point p1 = new Point(5, 7);
```

# `readonly struct`
The readonly modifier declares a structure immutable:
```cs
public readonly struct Point P { … }
```
If the struct is declared `readonly`, then:
1.  All fields must also be readonly
2.  All properties must be readonly (no `set` accessor) or init-only (`get, init` accessors)

## readonly instance members
Instead of declaring an entire struct immutable, you may declare some members immutable to indicate that they do not modify the state of the struct:
```cs
public readonly double Sum() => return X + Y;
public readonly override string ToString() => $"({X}, {Y})";
```

# nondestructive mutation
Use the `with` expression to mutate immutable properties or fields of a struct instance.
This creates a copy of th struct with the properties/fields modified:
```cs
var p1 = new Point(0, 0);
var p2 = p1 with { X = 1, Y = 3 };
```

# conversions
All structs, except `ref structs`, have boxing and unboxing conversions to/from `System.ValueType` and `System.Object`.
