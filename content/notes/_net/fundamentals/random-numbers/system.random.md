---
title: system.random
date: 2021-11-10T18:43:00-0700
draft: false
weight: 1
---

# Overview
Pseudo-random number generator.
- Documentation: https://learn.microsoft.com/en-us/_net/api/system.random?view=net-7.0

# Thread Safety
<r>Warning:</r> `System.Random` is not thread safe.

For concurrent operations across multiple threads, use `Random`'s `Shared` property which returns a thread-safe Random instance.

# Seeds
In .NET Core, `System.Random`'s default parameterless constructor uses a seed value produced by the thread-static random number generator itself.  It also has a constructor overload that accepts an `int` as a seed.

# Use
```cs
var bytes = new byte[5];
rand.NextBytes(bytes); // 5 random byte values.

rand.Next(); // Random integer.
rand.Next(101); // Random integer >= 0 and <= 100.
rand.Next(50, 101); // Random integer >= 50 and <= 100.

rand.NextSingle(); // Random floating point >= 0.0 and < 1.0.

rand.NextDouble(); // Random double > 0 and < 1.
rand.NextDouble(); // Random double > 0 and < 5.

rand.NextInt64(); // Non-negative random integer.
rand.NextInt64(101); // Non-negative random integer >= 0 and <= 100.
rand.NextInt64(50, 101); // Non-negative random integer >= 50 and <= 100.

rand.Sample(); // Random floating point number between 0.0 and 1.0.
```
