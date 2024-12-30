---
title: lists
date: 2021-11-13T11:21:00-0700
draft: false
weight: 1
---

# [Lists](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1?view=net-6.0)
Lists are ordered collections that can hold any object. Implements `IList<T>`. Allows for duplicate items.
Inherits from System.Collections.Generic implicitly.  
`List<T>` is not thread safe. Use `ImmutableList<T>` instead.  
For a heterogeneous collection of objects, use `List<Object>`.

# other lists
`SortedList<TKey, TValue>` A collection of key/value pairs that are sorted by key and accessible by key or index.

# creating
Declare a new List of strings:
```cs
var names = new List<string>Angle brackets are used for Generics.
// or
var names = new List<string> { "eli", "noah" }Declare and initialize (collection initializer).
```
# accessing
Lists can be indexed:
```cs
names[n]
name[^n] // return the nth item from the end of the list.
```

# properties
`.CountReturns` the number of elements in the List.

# methods
## manipulating
```cs
.Add(element) // Add element to List.
.AddRange(new[] { elem1, elem2, … }
.Remove(element) // Remove element from List.
```
## searching
```cs
.Contains(element)
.IndexOf(element) // Returns the index of element, or -1 if not found.
```
## sorting
```cs
.Sort() // Sorts the List in place.
```
