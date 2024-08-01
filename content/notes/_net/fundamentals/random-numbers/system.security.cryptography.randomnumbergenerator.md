---
title: system.security.cryptography.randomnumbergenerator
date: 2023-07-27T00:00:00-06:00
draft: false
weight: 1
---

# Overview
A cryptographically-secure random number generator.  Implements `IDisposable`.
- Documentation: https://learn.microsoft.com/en-us/dotnet/api/system.security.cryptography.randomnumbergenerator?view=net-7.0

# Use
Create a random number generator:
```cs
using System.Security.Cryptography;

using var rng = new RandomNumberGenerator.Create();

byte[5] fiveBytes = rng.GetBytes(5); // 5 random byte values.

var tenBytes = new byte[10];
rng.GetBytes(tenBytes); // Fills tenBytes with random byte values.

RandomNumberGenerator.GetInt32(11); // Random integer >= 0 and <= 10.
RandomNumberGenerator.GetInt32(-5, 6); // Random integer >= -5 and <= 5.

```
