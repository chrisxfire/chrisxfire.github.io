---
title: notes > dotnet > collections > generic > hashset
date: 2021-11-15T20:30:01-0700
draft: false
---
# [HashSet](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.hashset-1?view=net-6.0)
An unordered collection of unique items.

Namespace 
`Systems.Collections.Generic`
Inheritance 
`Object` -> `HashSet<T>`

# Construction
```cs
var hs = new HashSet<type>();
```
# Methods
```cs
.Add(elem) // Add elem to the set. Returns boolean if element was not already in the set.
.Contains(elem) // Return Boolean if elem is in the hashset.
