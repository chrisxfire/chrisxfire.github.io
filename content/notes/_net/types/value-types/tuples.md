---
title: tuples
date: 2021-11-05T21:38:53-0600
draft: false
weight: 1
tags:
 - kb/dotnet/types/value/tuples
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
```
… or …
```cs
var (v1, v2, …) = function();
```
… or …
```cs
type var1 = val1;
type var2 = val2;
(var1, var2) = function();
```

<g>Availability: C# 10</g>  
It is now possible to assign values to an existing variable and initialize newly declared variables in the same deconstruction:

```cs
int x = 0;
(x, int y) = point;
```
## Example
Store return value in a tuple with two named fields:
```cs
(string FruitName, int FruitQty) myFruit = GetNamedFruit();
Console.WriteLine(myFruit.FruitName); // output: "Apples"
Console.WriteLine(myFruit.FruitQty); // output: 5
```

Deconstruct the return value into two separate variables:
```cs
(string name, int num) = GetNamedFruit();
Console.WriteLine(name); // output: "Apples"
Console.WriteLine(num); // output: 5
```
