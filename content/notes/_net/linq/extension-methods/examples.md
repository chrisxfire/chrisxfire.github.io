---
title: examples
date: 2022-05-08T18:54:48-0600
draft: false
weight: 1
---
# `Where`
`Where` accepts a `Func<string, bool>` delegate. For each `string` passed to the function, it returns a `bool` value.

## Targeting a Named Method
```cs
static bool NameLongerThanFour(string name) => name.length > 4;

var query = names.Where(new Func<string, bool>(NameLongerThanFour));
```

Roslyn can instantiate the delegate for us so we can simplify:
```cs
var query = names.Where(NameLongerThanFour);
```

## Targeting a Lambda Expression
```cs
var query = names.Where(name => name.Length > 4);
```

# `OrderBy` & `ThenBy`
```cs
var query = names
    .Where(name => name.Length > 4)
    .OrderBy(name => name.Length) // Create groups of names of the same length;
    .ThenBy(name => name); // Within those groups, sort by name.
```

In query syntax:
```cs
var query = from name in names
    where name.Length > 4
    orderby name.Length, name
    select name; // In query syntax, `select` is always required.
```

# `OfType`
```cs
List<Object> objs = new() 
{
    new Person(),
    new Dog(),
    new House()
};

var query = objs.OfType<Dog>();
```
