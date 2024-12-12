---
title: deconstructors
date: 2021-12-31T10:31:57-0700
draft: false
weight: 1
tags:
 - kb/dotnet/types/classes/methods/deconstructors
---

# Deconstructors
The special method `Deconstruct()` is used to deconstruct a type:
```cs
public class Person 
{
    private string last;
    private string first;

    public Person(string lastName, string firstName) 
    {
        last = lastName;
        first = firstName;
    }

    public void Deconstruct(out string lname, out string fname) 
    {
        lname = lastName;
        fname = firstName;
    }
}

Person bob = new() { "eli", "smith" };
var (name1, name2) = eli;
Console.WriteLine(name1); // output: "eli"
Console.WriteLine(name2); // output: "smith"
```

# Overloaded Deconstructors
Overload deconstructors to allow callers to discard certain fields of the type.

For variables `var1`, `var2`, `var3`, …:
```cs
// … Constructor goes here …
public void Deconstruct(out type var1) 
{ // Discard var2 and var3
    xar1 = var1;
}

public void Deconstruct(out type var1, out type var2) 
{ // Discard var3 only
    xar1 = var1;
    xar2 = var2;
}
```
