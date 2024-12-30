---
title: dictionaries
date: 2021-11-13T11:20:41-0700
draft: false
weight: 1
---

# [Dictionary](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.dictionary-2?view=net-6.0#remarks)
A series of key-value pairs.
`Object` –> `Dictionary<TKey, TValue>`

Type safe. Invalid key throws exception.
Namespace  
`System.Collections.Generic`
Implements  
`IDictionary<TKey, TValue>`

Items in a dictionary are instances of a struct.

# other dictionaries
`SortedDictionary<TKey, TValue>` A collection of key/value pairs that are sorted by key.

# Construction`
```cs
Dictionary<key-type, value-type> d = new();
// or
Dictionary<TKey, TValue> d = new() 
{
    { key1, value1 }
    …
};
```
# accessing
`d[key]`

# iterating
```cs
foreach (KeyValuePair<TKey, TValue> item in d) 
{
    Console.WriteLine($"{item.Key}: {item.Value}");
}
```
# methods
## manipulating
```cs
.Add(key, value);
.Add(key: k, value: v);
```

## searching
```cs
.ContainsKey(key) // Return boolean if key is in dictionary.
.ContainsValue(value) // Return boolean if value is in dictionary.
.TryGetValue(key, out var1) // Retrieve value at key and store it in var1.
```

# properties
`.CountReturn` number of k:v pairs.
`.KeysReturn` the keys.
`.ValuesReturn` the values.
