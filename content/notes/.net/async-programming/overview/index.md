---
title: notes > .net > async programming > overview
date: 2022-02-16T00:00:00-06:00
draft: false
---

# Async
- Methods marked `async` can use `await` to designate suspension points.
- Async methods return to their caller when they encounter the first awaited object that's not yet complete, or they get to the end of the method, whichever occurs first.
- They can also be awaited by other methods that call it.
- They do not run on their own thread.

They trigger the C# compiler to transform the code into a state machine.
- They must have an `await` keyword in their body, or they will never yield, which wastes the expensive state machine.

An async void method is used only for event handlers:
- Such a method cannot be awaited.
- The caller of such a method cannot catch exceptiosns that the method throws.

# Threads and Tasks
`Thread` objects create new threads and manage them.  These can be difficult to work with.  
The `Task` class is a wrapper around a thread used for easier creation and management.

# `Task` and `Task<T>` Objects
`Task` and `Task<T>` are return types on async methods.  They hold information about the state of an asynchronous operation.  Eventually, they hold:
1. the final result from that operation —OR—
2. the exception that the operation raises.

Use `Task<T>` if the method has a return statement in which the operand has type `T` (like `return someInteger`).  
Use `Task` if the method has no return statement, or an empty return.  Common on `Main()` method.

`Task` is a reference type (it allocates an object).  Where possible, use `ValueTask`, which is a value type.

## Expression-Bodied Methods
If a method is expression-bodied, it can omit the async and await keywords:

```cs
static Task Main() => DoSomethingAsync();
```
…is equivalent to:
```cs
static async Task Main() 
{
	await DoSomethingAsync();
}
```
