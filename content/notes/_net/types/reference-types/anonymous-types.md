---
title: anonymous types
date: 2021-11-07T20:03:18-0700
draft: false
weight: 1
---

# anonymous types
Anonymous types are used to encapsulate a set of read-only properties into an object without having to define a type:
```cs
var v = new 
{
    Amount = 108, // Compiler infers Amount's type as `int`.
    Message = "Hello" // Compiler infers Message's type as `string`.
};
```
When a variable is initialized with an anonymous type, it must be declared as var to access the properties of the object at a later point.

# usage
Anonymous types are commonly used with properties from another type:
```cs
var productQuery =
    from prod in products
    select new 
    {
        prod.Color,
        prod.Price
    };

    foreach (var v in productQuery) 
    {
        Console.WriteLine("Color={0}, Price={1}", v.Color, v.Price);
    }

// Or an array of anonymously typed elements:
var anonArray = new[] { 
    new { name = "apple", diam = 4 }, 
    new { name = "grape", diam = 1 }
    };
```
