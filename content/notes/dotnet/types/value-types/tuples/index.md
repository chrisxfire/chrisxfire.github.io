---
title: "notes > dotnet > types > value types > tuples"
date: 2021-11-05T21:38:53-0600
draft: true
---
# Tuples
System.ValueTuple is modern; System.Tuple is legacy.

# Tuple
public (string, int) GetFruit() {
return ("Apples", 5)
}

var fruit = GetFruit();

The tuple's fields are automatically named Item1 and Item2:
fruit.Item1returns "Apples"
fruit.Item2returns 5

# Tuple with Named Fields
public (string Name, int Qty) GetNamedFruit() {
return (Name: "Apples", Qty: 5);
}

var namedFruit = GetNamedFruit();
namedFruit.Namereturns "Apples"
namedFruit.Qtyreturns 5

# Tuple Deconstruction
(*type v1*, *type v2*, …) = *function*();
… or …
var (*v1*, *v2*, …) = *function*();
… or …
*type var1* = *val1*
*type var2* = *val2*
(*var1*, *var2*) = *function*();

## Example
Store return value in a tuple with two named fields:
(string FruitName, int FruitQty) myFruit = GetNamedFruit();
myFruit.FruitNamereturns "Apples"
myFruit.FruitQtyreturns 5

Deconstruct the return value into two separate variables:
(string name, int num) = GetNamedFruit();
namereturns "Apples"
numreturns 5