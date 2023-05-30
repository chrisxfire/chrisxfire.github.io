---
title: "notes > dotnet > types > value types > structs"
date: 2021-11-05T21:23:37-0600
draft: true
---
# Structs
A value type that encapsulates data and related functionality.

## Characteristics
- Allocation:Stack
- Equality: Value (albeit inefficient)
- Semantics: Value (a variable of a struct type contains an instance of that type)
- Inheritance: None (sealed)
- Mutability: Mutable (but, recommended to be made immutable with `readonly` modifer)

## Use When
- You need a small, data-centric type with little or no behavior
- You need a type whose fields are only value types
- The total bytes used by all the fields in the type is 16 bytes or less
- .NET uses structs for numbers, booleans, unicode chars, time.

# Creating
Note: When creating custom structs, always override ToString() to provide information about the type (not shown here).

public struct Point {
public double X { get; }
public double Y { get; }
public Point(double x, double y) => (X, Y) = (x, y);

public override string ToString() => $"({X}, {Y})";
}

## <u>Initialization</u>
Uninitailized fields are assigned their default value.

If all instance fields of a struct are accessible, the struct can be instantiated without the `new` operator.

## <u>Creating Objects</u>
Point p1 = new Point(5, 7);

# readonly struct
The readonly modifier declares a structure immutable:
public readonly struct Point P { … }

If the struct is declared readonly, then:
1.  All fields must also be readonly
2.  All properties must be readonly (no `set` accessor) or init-only (`get, init` accessors)

## <u>readonly instance members</u>
Instead of declaring an entire struct immutable, you may declare some members immutable to indicate that they do not modify the state of the struct:
public readonly double Sum() => return X + Y;
public readonly override string ToString() => $"({X}, {Y})";

# Nondestructive mutation
Use the with expression to mutate immutable properties or fields of a struct instance.
This creates a copy of th struct with the properties/fields modified:
var p1 = new Point(0, 0);
var p2 = p1 with { X = 1, Y = 3 };

# Conversions
All structs, except `ref structs`, have boxing and unboxing conversions to/from `System.ValueType` and `System.Object`.