---
title: objects
date: 2021-11-09T20:44:08-0700
draft: false
weight: 1
---

# objects
Because all objects implicitly inherit from `Object`, they have these methods:
- `ToString()` — Converts the class object to a string representation.
- `GetHashCode()` — Returns the unique hash code of the object.
- `GetType()` — Returns the Type of the object which represents its class.

# creating
new() allocates memory, invokes a constructor, and returns a reference to the instance:

```cs
SomeClass variable = new();
var variable = new Class(arg1, arg2, …);
var p1 = new Point(0, 0);
var p2 = new Point(10, 20);
```

# Checking the Type of an Object (`is` Keyword)
Use the `is` keyword:
```cs
if (alice is Employee) { … }
```

# Casting an Object (`as` Keyword)
Use the `as` keyword to cast an object to another type:
```cs
Employee? alice = someAlice as Employee; // The as keyword returns null if the type cannot be cast.
```
