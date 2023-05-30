---
title: "notes > dotnet > classes > expression bodied members"
date: 2022-02-16T16:38:07-0700
draft: true
---
Expression-Bodied Members
Expression body definitions are a concise form of implementing a member.

## <u>Usage</u>
*member* => *expression*;

## <u>Use in Methods</u>
Commonly used in types that override the ToString method:
public override string ToString() => $"{fname} {lname}".Trim();

## <u>Use in Read Only Properties</u>
public class Location {
private string locationName;

public Location(string name) {
locationName = name;
}

public string Name => locationName;
}

## <u>Use in Constructors and Properties</u>
public class Location {
private string locationName;

public Location(string name) => Name = name; // Assigns argument *name* to property *Name*.

public string Name {
get => locationName; // Equivalent to get { return locationName; }
set => locationName; // Equivalent to set { locationName = name } = value;(?)
}
}