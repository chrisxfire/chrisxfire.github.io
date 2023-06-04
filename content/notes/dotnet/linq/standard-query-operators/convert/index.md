---
title: "notes > dotnet > linq > standard query operators > convert"
date: 2022-11-13T18:58:51-0700
draft: false
---
Convert methods change the type of objects.

# Methods
`As*` methods change the static type of the collection but do not enumerate it.  
`To*` methods enumerate the collection and put the items into a different collection type.

| Methods        | Description                                                                                               | Query expression         |
| -------------- | --------------------------------------------------------------------------------------------------------- | ------------------------ |
| `AsEnumerable` | Returns the input typed as IEnumerable<T>                                                                 | N/A                      |
| `AsQueryable`  | Converts an IEnumerable to IQueryable                                                                     | N/A                      |
| `Cast`         | Casts the elements of a collection to a new type                                                          | from <type> var in words |
| `OfType`       | Selects values depending on their ability to be cast to the specified type                                | N/A                      |
| `ToArray`      | Convert a collection to an array (forces query execution)                                                 | N/A                      |
| `ToDictionary` | Puts elements into a `Dictionary<TKey, TValue>` based on a key-selector function (forces query execution) | N/A                      |
| `ToList`       | Convert a collection to a `List<T>` (forces query execution)                                              | N/A                      |
| `ToLookup`     | Puts elements into a `Lookup<TKey, TValue>` based on a key-selector function (forces query execution)     | N/A                      |
