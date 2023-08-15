---
title: ref structs
date: 2022-11-03T20:34:52-0600
draft: false
weight: 1
---
# [ref Structs](https://learn.microsoft.com/en-us/_net/csharp/language-reference/builtin-types/ref-struct)
Instances of a `ref` struct are allocated on the stack and cannot escape to the managed heap.

Restrictions:
- A `ref` struct cannot implement interfaces
- A `ref` struct cannot be a type argument
- A `ref` struct variable cannot be captured via lambda expression or local function
- A `ref` struct variable cannot be used in an async method (but can be used in a synchronous method that return `Task/Task<T>`)

## Disposable
A ref struct can be made disposable: create an instance or extension Dispose method that is accessible, parameterless, and returns void.

## `ref` Fields
<g>Availability: C# 11</g>  
- May hold null. Use `Unsafe.IsNullRef<T>(T)` to determine if a ref field is null.

# `ref readonly`
The `readonly` modifier affects the expression to its right:
```cs
ref readonly int someVar; // someVar cannot receive a new value.
readonly ref int someVar; // someVar cannot refer to another object.
readonly ref readonly int someVar; // someVar cannot receive a new value and cannot receive refer to another object.
```

# s`coped ref`
Adding the `scoped` modifier asserts that code will not extend the lifetime of a variable.
