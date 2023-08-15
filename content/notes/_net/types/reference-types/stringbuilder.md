---
title: stringbuilder
date: 2021-11-11T16:38:01-0700
draft: false
weight: 1
---
# [StringBuilder](https://docs.microsoft.com/en-us/_net/api/system.text.stringbuilder?view=net-6.0)
`Object` –> `StringBuilder`  

# Construction
```cs
var sb = new StringBuilder("string"); // string is optional.
var sb = new StringBuilder("string", initial_capacity);
var sb = new StringBuilder(initial_capacity, max_capacity);
```

# Properties
- `Chars`[index] — Return or set the character at index.
- `Length` — Current number of characters in the StringBuilder.
- `Capacity` — Number of characters that the StringBuilder can currently hold.  This is increased dynamically.
- `MaxCapacity` — By default, set to Int32.MaxValue. Can be overwritten.

# Methods
## Manipulating
These methods accept a string, substring, character array, or the string representation of a primitive data type:
- `Append("substr")` — Append substr to the StringBuilder.
- `AppendJoin(sep, "str[]")` — Concatenate str array with sep between each string and append to the StringBuilder.
- `AppendLine("substr")` — Append substr and \r\n to the StringBuilder.
- `Insert(index, "str")` — Insert str at index.
- `Replace("old," "new")` — Replace old with new.

## Deleting
- `Clear()` — Empties the StringBuilder and sets Length to 0.
- `Remove(index, n)` — Removes n characters from StringBuilder starting at index.

## Miscellaneous
`.EnsureCapacity(n)` — Ensure the capacity of the StringBuilder is at least n. If not, expand it.  
`.ToString()` — Returns the built string. 
