---
title: notes > .net > collections > overview
date: 2022-02-16T16:22:14-0700
draft: false
---
# [Collections](https://docs.microsoft.com/en-us/dotnet/api/system.collections?view=net-6.0)
Collections of objects.

# Namespaces
System.Collections — .NET Framework 1.0; Legacy;
System.Collections.Generic — .NET Framework 2.0; no thread synchronization
System.Collections.Concurrent — .NET Framework 4.0; thread-safe

# Common Features
All collections implement the ICollection/<T> interface. This means they must have a Count property.
All collections implement the IEnumerable/<T> interface, which allows them to be iterated over with foreach.
- This interface requires GetEnuemrator(), which returns an object that implements IEnumerator.
  - The IEnumerator object must have methods MoveNext() and Reset() and property Current that contains the current item in the collection.

# Choosing a Collection
<table>
<colgroup>
<col style="width: 7%" />
<col style="width: 17%" />
<col style="width: 21%" />
<col style="width: 24%" />
<col style="width: 28%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>A collection of…</strong></th>
<th><strong>Generic collection</strong></th>
<th><strong>Sorted counterpart?</strong></th>
<th><strong>Thread-safe counterpart?</strong></th>
<th><strong>Immutable counterpart?</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Key/value pairs accessed</p>
<p>by key</p></td>
<td>Dictionary&lt;TKey,TValue&gt;</td>
<td><p>SortedDictionary&lt;TKey,TValue&gt;</p>
<p></p></td>
<td>ConcurrentDictionary&lt;TKey,TValue&gt;</td>
<td><p>ImmutableDictionary&lt;TKey,TValue&gt;</p>
<p>ImmutableSortedDictionary&lt;TKey,TValue&gt;</p></td>
</tr>
<tr class="even">
<td><p>Elements accessed</p>
<p>by index</p></td>
<td>List&lt;T&gt;</td>
<td><p>SortedList&lt;TKey,TValue&gt;</p>
<p></p></td>
<td>ConcurrentBag&lt;T&gt;</td>
<td><p>ImmutableList&lt;T&gt;</p>
<p>ImmutableArray</p></td>
</tr>
<tr class="odd">
<td>Elements in FIFO order</td>
<td>Queue&lt;T&gt;</td>
<td>N/A</td>
<td>ConcurrentQueue&lt;T&gt;</td>
<td>ImmutableQueue&lt;T&gt;</td>
</tr>
<tr class="even">
<td>Elements in LIFO order</td>
<td>Stack&lt;T&gt;</td>
<td>N/A</td>
<td>ConcurrentStack&lt;T&gt;</td>
<td>ImmutableStack&lt;T&gt;</td>
</tr>
<tr class="odd">
<td><p>Elements sorted</p>
<p>head—&gt;tail or tail—&gt;head</p></td>
<td>LinkedList&lt;T&gt;</td>
<td>N/A</td>
<td>None</td>
<td>N/A</td>
</tr>
<tr class="even">
<td>Unique items</td>
<td>HashSet&lt;T&gt;</td>
<td>SortedSet&lt;T&gt;</td>
<td>None</td>
<td><p>ImmutableHashSet&lt;T&gt;</p>
<p>ImmutableSortedSet&lt;T&gt;</p></td>
</tr>
</tbody>
</table>

## Notes
- A `SortedDictionary<TKey,TValue>` performs better than a `SortedList<TKey,TValue>` at the expense of more memory used.
- For `Queues` and `Stacks`, elements are generally discarded after they are accessed.
# 
# Other Collections
| Collection               | Use when you need…                                                     |
|------------------------------|----------------------------------------------------------------------------|
| BlockingCollection<T>      | a thread-safe collection that blocks Add/Take operations when full/empty   |
| HybridDictionary             | a ListDictionary when collection is small; a Hashtable when it grows large |
| LinkedList<T>              | a collection with elements sorted head —> tail or tail —> head           |
| NameValueCollection          | a collection with one key, multiple values                                 |
| ObservableCollection<T>    | a collection that provides notification when items are added/removed       |
| OrderedDictionary            | a collection whose elements can be accessed by both key and index          |
| PriorityQueue<TKey,TValue> | a collection of elements and a priority                                    |
| StringCollection             | a list of only strings                                                     |
| StringDictionary             | a dictionary of only strings                                               |


# Algorithmic Complexity
| Mutable               | Amortized | Worst Case          | Immutable                      | Complexity |
|---------------------------|---------------|-------------------------|------------------------------------|----------------|
| Stack<T>.Push           | O(1)          | O(n)                    | ImmutableStack<T>.Push           | O(1)           |
| Queue<T>.Enqueue        | O(1)          | O(n)                    | ImmutableQueue<T>.Enqueue        | O(1)           |
| List<T>.Add             | O(1)          | O(n)                    | ImmutableList<T>.Add             | O(logn)       |
| List<T>.Item[Int32]   | O(1)          | O(1)                    | ImmutableList<T>.Item[Int32]   | O(logn)       |
| List<T>.Enumerator      | O(n)          | O(n)                    | ImmutableList<T>.Enumerator      | O(n)           |
| HashSet<T>.Add, lookup  | O(1)          | O(n)                    | ImmutableHashSet<T>.Add          | O(logn)       |
| SortedSet<T>.Add        | O(logn)      | O(n)                    | ImmutableSortedSet<T>.Add        | O(logn)       |
| Dictionary<T>.Add       | O(1)          | O(n)                    | ImmutableDictionary<T>.Add       | O(logn)       |
| Dictionary<T>lookup    | O(1)          | O(1) – or strictly O(n) | ImmutableDictionary<T>lookup    | O(logn)       |
| SortedDictionary<T>.Add | O(logn)      | O(nlogn)              | ImmutableSortedDictionary<T>.Add | O(logn)       |

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
