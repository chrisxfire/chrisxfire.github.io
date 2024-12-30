---
title: stacks
date: 2021-11-15T16:42:50-0700
draft: false
weight: 1
---

# [Stack](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.stack-1?view=net-6.0)
A last-in, first-out collection of objects.  
![](./stack.png)

## namespace
`Systems.Collections.Generic`

## inheritance
`Object` –> `Stack<T>`

# construction
```cs
var stk = new Stack<type>();
```
# methods
```cs
.Peek() // Return, but do not remove, the element at the top of the stack.
Throws exception on empty stack.
.Pop() // Remove and return the element at the top of the stack.
.Push(elem) // Push elem onto stack.
.TryPeek(out var1) // Return, but do not remove, the element at the top of the stack and store it in var1. Return boolean if peek was successful.
```
