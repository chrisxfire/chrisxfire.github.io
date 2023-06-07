---
title: "notes > dotnet > system > random"
date: 2021-11-10T18:43:00-0700
draft: true
---
[System.Random](https://docs.microsoft.com/en-us/dotnet/api/system.random?view=net-6.0)
Object –> Random
Psuedo-random number generator.

# Construction
var rand = new Random*(int);*Optional *int* as a seed.

# Methods
var bytes = new byte[5];
rand.NextBytes(bytes);5 random byte values.

rand.Next();Random integer.
rand.Next(101);Random integer >= 0 and <= 100.
rand.Next(50, 101);Random integer >= 50 and <= 100.

rand.NextSingle()Random floating point >= 0.0 and < 1.0.

rand.NextDouble();Random double > 0 and < 1.
rand.NextDouble() * 5;Random double > 0 and < 5.

rand.NextInt64()Non-negative random integer.
rand.NextInt64(101)Non-negative random integer >= 0 and <= 100.
rand.NextInt64(50, 101)Non-negative random integer >= 50 and <= 100.