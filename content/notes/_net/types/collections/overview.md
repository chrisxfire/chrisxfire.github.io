---
title: overview
date: 2022-02-16T16:22:14-0700
draft: false
weight: -1
---

# Collections
- Collections of objects.
- Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.collections?view=net-6.0

# Namespaces
- `System.Collections` — .NET Framework 1.0; Legacy;
- `System.Collections.Generic` — .NET Framework 2.0; no thread synchronization
- `System.Collections.Concurrent` — .NET Framework 4.0; thread-safe

# Common Features
- All collections implement the `ICollection/<T>` interface. This means they must have a `Count` property.
- All collections implement the `IEnumerable/<T>` interface, which allows them to be iterated over with foreach.
  - This interface requires `GetEnuemrator()`, which returns an object that implements `IEnumerator`.
    - The IEnumerator object must have methods `MoveNext()` and `Reset()` and property `Current` that contains the current item in the collection.

# Choosing a Collection
| A collection of…                           | Generic collection        | Sorted counterpart?             | Thread-safe counterpart?            | Immutable counterpart?                                                       |
| ------------------------------------------ | ------------------------- | ------------------------------- | ----------------------------------- | ---------------------------------------------------------------------------- |
| Key/value pairs accessed by key            | `Dictionary<TKey,TValue>` | `SortedDictionary<TKey,TValue>` | `ConcurrentDictionary<TKey,TValue>` | `ImmutableDictionary<TKey,TValue>`, `ImmutableSortedDictionary<TKey,TValue>` |
| Elements accessed by index                 | `List<T>`                 | `SortedList<TKey,TValue>`       | `ConcurrentBag<T>`                  | `ImmutableList<T>`, `ImmutableArray`                                         |
| Elements in FIFO order                     | `Queue<T>`                | N/A                             | `ConcurrentQueue<T>`                | `ImmutableQueue<T>`                                                          |
| Elements in LIFO order                     | `Stack<T>`                | N/A                             | `ConcurrentStack<T>`                | `ImmutableStack<T>`                                                          |
| Elements sorted head—> tail or tail—> head | `LinkedList<T>`           | N/A                             | None                                | N/A                                                                          |
| Unique items                               | `HashSet<T>`              | `SortedSet<T>`                  | None                                | `ImmutableHashSet<T>`, `ImmutableSortedSet<T>`                               |

## Notes
- A `SortedDictionary<TKey,TValue>` performs better than a `SortedList<TKey,TValue>` at the expense of more memory used.
- For `Queues` and `Stacks`, elements are generally discarded after they are accessed.
 
# Other Collections
## `System.Collections.ObjectModel`
Use these collections when properties or methods return collections:
| Collection                         | Description                                                                                 |
| ---------------------------------- | ------------------------------------------------------------------------------------------- |
| `Collection<T>`                    | Base class for a generic collection                                                         |
| `KeyedCollection<TKey, TItem>`     | Abstract base class for a collection whose keys are embedded in the values                  |
| `ObservableCollection<T>`          | Provides notifications when items get added or removed, or when the whole list is refreshed |
| `ReadOnlyCollection<T>`            | Base class for a generic read-only collection                                               |
| `ReadOnlyDictionary<TKey, TValue>` | A read-only, generic collection of key/value pairs                                          |
| `ReadOnlyObservableCollection<T>`  | A read-only ObservableCollection<T>                                                         |

## Others...
| Collection                   | Use when you need…                                                         |
| ---------------------------- | -------------------------------------------------------------------------- |
| `BlockingCollection<T>`      | a thread-safe collection that blocks Add/Take operations when full/empty   |
| `HybridDictionary`           | a ListDictionary when collection is small; a Hashtable when it grows large |
| `LinkedList<T>`              | a collection with elements sorted head —> tail or tail —> head             |
| `NameValueCollection`        | a collection with one key, multiple values                                 |
| `OrderedDictionary`          | a collection whose elements can be accessed by both key and index          |
| `PriorityQueue<TKey,TValue>` | a collection of elements and a priority                                    |
| `StringCollection`           | a list of only strings                                                     |
| `StringDictionary`           | a dictionary of only strings                                               |

# Algorithmic Complexity
| Mutable                   | Amortized | Worst Case              | Immutable                          | Complexity |
| ------------------------- | --------- | ----------------------- | ---------------------------------- | ---------- |
| `Stack<T>.Push`           | O(1)      | O(n)                    | `ImmutableStack<T>.Push`           | O(1)       |
| `Queue<T>.Enqueue`        | O(1)      | O(n)                    | `ImmutableQueue<T>.Enqueue`        | O(1)       |
| `List<T>.Add`             | O(1)      | O(n)                    | `ImmutableList<T>.Add`             | O(logn)    |
| `List<T>.Item[Int32]`     | O(1)      | O(1)                    | `ImmutableList<T>.Item[Int32]`     | O(logn)    |
| `List<T>.Enumerator`      | O(n)      | O(n)                    | `ImmutableList<T>.Enumerator`      | O(n)       |
| `HashSet<T>.Add`, lookup  | O(1)      | O(n)                    | `ImmutableHashSet<T>.Add`          | O(logn)    |
| `SortedSet<T>.Add`        | O(logn)   | O(n)                    | `ImmutableSortedSet<T>.Add`        | O(logn)    |
| `Dictionary<T>.Add`       | O(1)      | O(n)                    | `ImmutableDictionary<T>.Add`       | O(logn)    |
| `Dictionary<T>lookup`     | O(1)      | O(1) – or strictly O(n) | `ImmutableDictionary<T>lookup`     | O(logn)    |
| `SortedDictionary<T>.Add` | O(logn)   | O(nlogn)                | `ImmutableSortedDictionary<T>.Add` | O(logn)    |

# Construction
```cs
var collection = new CollectionType<GenericType>();
```
or
```cs
var collection = new CollectionType<GenericType>{ item1, item2, … }
```
or
```cs
public class Galaxy 
{
    public string Name { get; set; }
    public int MegaLightYears { get; set; }
}

var theGalaxies = new CollectionType<Galaxy> 
{
    new Galaxy() { Name="Andromeda", MegaLightYears=3 },
    …
}
```

# Collection Initializers
Collection initializers let you specify one or more element initializers when you initialize a collection type that implements IEnumerable and has an Add method:
```cs
List<int> digits = new List<int> { 0, 1, 2, 3 };
```

## Combining Collection Initializers with Object Initializers
```cs
List<Cat> cats = new List<Cat> 
{
    new Cat{ Name = "Silvester", Age = 2 };
    new Cat{ Name = "Tom", Age = 9 };
}
```
# Iterating
```cs
for (var variable in collection) { … }
```
or
```cs
for (var index = 0; index < collection.Count; index++) { … }
```

# Methods
## Manipulating
```cs
collection.Add(element)
collection.Remove(element)
collection.RemoveAt(index)Elements after the one that are removed now have a lower index value.
```

# Defining Custom Collections
It is usually better to use the .NET collections.  
Implement either `IEnumerable` or `IEnumerable<T>`:
```cs
public class DaysOfTheWeek : IEnumerable 
{
    private string[] days = { "Sun", "Mon", "Tue", … }

    public IEnumerator GetEnumerator() 
    { // IEnumerable requires GetEnumerator() to be implemented.
        for (int index = 0; index < days.Length; index++) 
        {
            yield return days[index];
        }
    }
}
```
