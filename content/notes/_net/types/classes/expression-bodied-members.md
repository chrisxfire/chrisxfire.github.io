---
title: expression bodied members
date: 2022-02-16T16:38:07-0700
draft: false
weight: 1
---

# Expression-Bodied Members
Expression body definitions are a concise form of implementing a member.

## usage
```cs
member => expression;
```

## use in methods
Commonly used in types that override the ToString method:
```cs
public override string ToString() => $"{fname} {lname}".Trim();
```

## use in read only properties
```cs
public class Location {
    private string locationName;

    public Location(string name) 
    {
        locationName = name;
    }

    public string Name => locationName;
}
```

## use in constructors and properties
```cs
public class Location 
{
    private string locationName;

    public Location(string name) => Name = name; // Assigns argument name to property Name.

    public string Name 
    {
        get => locationName; // Equivalent to get { return locationName; }
        set => locationName; // Equivalent to set { locationName = name } = value;(?)
    }
}
```
