---
title: compilation statements
date: 2022-01-01T00:00:00-06:00
draft: false
weight: 1
---

# compilation statements
Compilation statements allow code to be written that only compiles if the conditional is true.

Modern .NET Symbols:
`NET6_0`
`NET6_0_ANDROID`
`NET6_0_IOS`
`NET6_0_WINDOWS`

```cs
#if NET6_0_ANDROID
// compile statements that only work on Android

#elif NET6_0_IOS
// compile statements that only work on iOS

#else
// compile statements that work everywhere else
```
