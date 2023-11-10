---
title: argument matching
date: 2023-10-30T00:00:00-06:00
draft: false
weight: 1
---

# Overview [[Documentation](https://nsubstitute.github.io/help/argument-matchers/)]  

Argument matchers provide a way to:
1. specify a call or group of calls so that a return value can be set for all matching calls
2. check a matching call has been received

Argument matchers can be used:
1. when setting return values (with a call to `Returns()`)
2. when validating calls (with a call to `Received()`)

# Uses
## Ignoring Arguments
Use `Arg.Any<T>()` to ignore an argument of type `T`:
```cs
calculator.Add(Arg.Any<int>(), 5).Returns(7);

Assert.AreEqual(7, calculator.Add(42, 5));
Assert.AreEqual(7, calculator.Add(123, 5)); 
Assert.AreNotEqual(7, calculator.Add(1, 7)); 
```

## Match an Argument
Use `Arg.Is<T>(T value)` to match an argument of type `T`:
```cs
calculator.Add(0, 42);
calculator.Received().Add(Arg.Is(0), Arg.Any<int>());
```

## Conditionally Match an Argument
Use `Arg.Is<T>(Predicate<T> condition)` to conditionally match an argument of type `T`:
```cs
calculator.Add(1, -10);

// Received call with first arg 1 and second arg less than 0:
calculator.Received().Add(1, Arg.Is<int>(x => x < 0));

// Received call with first arg 1 and second arg of -2, -5, or -10:
calculator.Received().Add(1, Arg.Is<int>(x => new[] {-2,-5,-10}.Contains(x)));

// Did not receive call with first arg greater than 10:
calculator.DidNotReceive().Add(Arg.Is<int>(x => x > 10), -10);
```

## Match `out` and `ref` Arguments
```cs
calculator.LoadMemory(1, out Arg.Any<int>())
          .Returns(x => 
          {
              x[1] = 42;
              return true;
          });

var hasEntry = calculator.LoadMemory(1, out var memoryValue);

Assert.AreEqual(true, hasEntry);
Assert.AreEqual(42, memoryValue);
```