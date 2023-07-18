---
title: notes > .net > types > value types > tuples
date: 2021-11-05T21:38:53-0600
draft: false
weight: 1
---
# Tuples
`System.ValueTuple` is modern; `System.Tuple` is legacy.

# Tuple
```cs
public (string, int) GetFruit() 
{
    return ("Apples", 5)
}

var fruit = GetFruit();
```

The tuple's fields are automatically named Item1 and Item2:
```cs
fruit.Item1 // returns "Apples"
fruit.Item2 // returns 5
```

# Tuple with Named Fields
```cs
public (string Name, int Qty) GetNamedFruit() 
{
    return (Name: "Apples", Qty: 5);
}

var namedFruit = GetNamedFruit();
namedFruit.Name // returns "Apples"
namedFruit.Qty // returns 5
```

# Tuple Deconstruction
```cs
(type v1, type v2, …) = function();
// … or …
var (v1, v2, …) = function();
// … or …
type var1 = val1;
type var2 = val2;
(var1, var2) = function();
```

## Example
Store return value in a tuple with two named fields:
```cs
(string FruitName, int FruitQty) myFruit = GetNamedFruit();
myFruit.FruitName // returns "Apples"
myFruit.FruitQty // returns 5

// Deconstruct the return value into two separate variables:
(string name, int num) = GetNamedFruit();
name // returns "Apples"
num // returns 5
```
