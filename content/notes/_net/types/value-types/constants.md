---
title: constants
date: 2022-02-19T11:32:28-0700
draft: false
weight: 1
---

# constant
Constants – immutable values known at compile time which do not change.
- Only built-in types may be declared const.
- Constants cannot be declared static (this would be redundant).

## use
Constants are used instead of *magic numbers* to provide meaningful names for special values.

## constant integrals
Instead of a constant `int`, `byte`, etc, use an `enum`.

## best practice
Constants can be grouped in a single, static class named Constants. This helps ensure those who use the constant understand it is constant and cannot be modified:

```cs
public static class Constants 
{
    public const double Pi = 3.141592653589793;
    public const int SpeedOfLight = 3000000; // km per second.
}
```

# Constant vs. Readonly
A `const` value is declared once at compile time and never changed.
A `readonly` value is declared once at runtime by a constructor and never changed.
