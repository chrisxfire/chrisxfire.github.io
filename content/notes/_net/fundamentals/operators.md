---
title: notes > .net > fundamentals > operators
date: 2022-01-02T00:00:00-06:00
draft: false
weight: 1
---

# Operators
Unary operators work on a single operand:
```cs
int y = x++;
```

Binary operators work on two operands:
```cs
int sum = x + y;
```

Ternary operators (`?:`) work on three operands.

# Built-in Operators
## `nameof()`
`nameof()` returns the name of a variable, type or member as a string constant:
```cs
nameof(numbers) //returns numbers
nameof(numbers.Count) //returns Count
```

## `sizeof()`
`sizeof()` returns the number of bytes that an instance of a type uses in memory:
```cs
sizeof(obj)
```

## `typeof()`
`typeof()` returns the System.Type instance of a type.
```cs
typeof(arg) // where arg is the name of a type or type parameter.
 // arg cannot be dynamic or any nullable reference type.
typeof(List<string>) // returns System.Collection.Generic.List`1[System.String]
typeof(int) // returns System.Int32
```

## `default()`
`default()` returns the default value of a type:
```cs
default(int) // returns 0
int number = default // sets number to 0
```

# `is` Operator
Check if the runtime type of an expression is compatible with a given type.
Also tests an expression result against a pattern.
```cs
Expression is Type
```

# `as` Operator
Explicitly convert an expression to a given reference or nullable type.
```cs
Expression as Type
```

# Other Operators
`=` assignment operator
`.` member access operator
`()` invocation operator
`[]` indexer access operator

# Lambda Operator
Normal method definition:
```cs
public override string ToString()
{
    return $"{fname} {lname}".Trim();
}
```

Lambda:
```cs
public override string ToString() => $"{fname} {lname}".Trim
```

# NOOP
The noop keyword in C# is `;` (a standalone semi-colon).

# Implementing Operators
Use the operator keyword to define a static method for an operator to implement it:
```cs
public static Person operator *(Person p1, Person p2) {
    return Person.Procreate(p1, p2);
}

Person dad = new();
Person mom = new();
Person baby = mom * dad;
```

Note: For every operator you define, define a method as well.  Give developers the option.
