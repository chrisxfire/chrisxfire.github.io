---
title: notes > code > .net > classes > methods > local functions
date: 2022-01-02T20:27:50-0700
draft: false
weight: 1
---
# Local Functions
Methods that are only accessible from within the containing method in which they are defined.  
They can be declared and called from methods (especially iterator and async methods), constructors, property accessors, event accessors, anonymous methods, lambda expressions, finalizers, and other local functions.  

# Modifiers
Local functions support the following modifiers:
- `async`
- `unsafe`
- `static`
  - A static local function cannot capture local variables or instance state.
- `extern`
  - An external local function must be static.

All local functions are intrinsicly private.

# Variables in Local Functions
All local variables that are defined in the containing member, including its method parameters, are accessible to a local function (so long as it is not a static local function).

# Attributes in Local Functions
Attributes can be applied to a lcoal function, its parameters, and type parameters:
```cs
private static void Process(string?[] lines, string mark) 
{
  // …

  bool IsValid([NotNullWhen(true)] string? line) 
  {
    // …
  }
}
```

# Exceptions in Local Functions
Local functions can allow exceptions to surface immediately. This makes them especiall useful in:
- Method iterators, where exceptions are only surfaced when the returned sequence is enumerated, not when the iterator is retrieved (when the IEnumerable is instantiated).
- Async methods, where exceptions thrown are not observed until the returned task is awaited.

# Local Functions vs. Lambda Expressions
Local functions and lambda expressions are similar. Key differences:

## Naming
Local functions are explicitly named, like methods.  
Lambda expressions are anonymous methods and need to be assigned to variables of a delegate type, like Action or Func types.  
- Lambda expressions rely on the return type of the Action/Func variable to which they are assigned to determine their argument and return types.

## Definition
Local functions: defined at compile time (this is why they can be declared above or below return statements)  
Lambda expressions: declared and assigned at run time.  

## Recursive Algorithms
Recursive algorithms are easier to create using local functions.  

## Delegates
Lambda expressions are converted to delegates when they're declared.  
Local functions can be written either as methods or delegates. They are only converted to delegates when they are *used* as a delegate.  

## Heap Allocations
Local functions can avoid heap allocations that are always necessary for lambda expressions. If a local function is never converted to a delegate, the compiler avoids a heap allocation.  

## Iterators
Local functions can be implemented as iterators using yield return to produce a sequence of values.

# Example
```cs
public static int Factorial(int number) 
{
  if (number < 0) 
  {
    throw new ArgumentException(…);
  }

  return localFactorial(number);

  int localFactorial(int localNumber) 
  { // Local function.
    if (localNumber < 1) { return 1; }
    return localNumber * localFactorial(localNumber - 1);
  }
}
```
