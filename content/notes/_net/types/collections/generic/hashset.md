---
title: hashset
date: 2021-11-15T20:30:01-0700
draft: false
weight: 1
---

# [HashSet](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.hashset-1?view=net-6.0)
An unordered collection of unique items.

Namespace 
`Systems.Collections.Generic`
Inheritance 
`Object` -> `HashSet<T>`

# construction
```cs
var hs = new HashSet<type>();
```
# methods
```cs
.Add(elem) // Add elem to the set. Returns boolean if element was not already in the set.
.Contains(elem) // Return Boolean if elem is in the hashset.
