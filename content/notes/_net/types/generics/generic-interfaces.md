---
title: notes > .net > types > generics > generic interfaces
date: 2023-07-17T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Generic interfaces are type-safe counterparts to nongeneric interfaces for ordering and equality comparisons and for functionality shared by generic collection types.
- <g>Availability: .NET 7</g>

# Framework-provided Generic Interfaces
## For Equality and Ordering Comparisons
- `System.IComparable<T>` — methods for ordering comparisons
- `System.IEquatable<T>` — methods for equality comparisons
- `IComparer<T>` — define an ordering comparison for types that do not implement `IComparable<T>`
- `IEqualityComparer<T>` — define an equality comparison for types that do not implement `IEquatable<T>`

## For Collection Functionality
- `ICollection<T>` — the basic interface for generic collection types; methods for adding, removing, copying, and enumerating elements; inherits from `IEnumerable<T>` and `IEnumerable`.
- `IList<T>` — extends `ICollection<T>` with methods for indexed retrieval
- `IDcitionary<TKey, TValue>` — extends `ICollection<T>` with methods for keyed retrieval
- `IEnumerable<T>` — provides a generic enumerator structure; inherits `IEnumerator`, so any consumer of the nongeneric interface can also consume this generic one