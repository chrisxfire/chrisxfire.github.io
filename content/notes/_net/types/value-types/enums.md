---
title: enums
date: 2021-11-05T21:33:38-0600
draft: false
weight: 1
---

# [Enums](https://docs.microsoft.com/en-us/dotnet/api/system.enum?view=net-6.0)
`System.ValueType` –> `System.Enum`  

Enums store choices that are optionally related to values.  
Enums are thread safe.

# Best Practices
- If there is no enum member with value 0, create a `None` constant.
  - (The memory used for the enum is initialized to 0 by the CLR. If you do not define a constant whose value = 0, the enum will contain an illegal value when created.)
- When you define a method or property that takes an enum constant as a value, validate the value.
  - (A numeric value casted to the enum type will succeed even if that numeric value is not defined in the enum.)

# Creating
```cs
public enum Weekdays { Monday, Tuesday, Wednesday, Thursday, Friday }

public enum Seasons
{
  None = 0,
  Summer = 1,
  Autumn = 2,
  Winter = 4,
  Spring = 8,
  All = Summer | Autumn | Winter | Spring
}

Seasons.All returns Summer, Autumn, Winter, Spring
```
# Declaring
```cs
var theYear = Seasons.All;
```
# Operators
The bitwise operators `|` and `&` are used to combine and intersect enum choices:
```cs
var warmTimes = Seasons.Spring & Seasons.Summer;
var startingOnEquinox = Seasons.Spring | Seasons.Autumn;
```

# Conversions
Enums can be explicitly casted to their underlying integral type:
```cs
public enum ArrivalStatus { Late = -1, OnTime = 0, Early = 1 };

int value3 = 2;
ArrivalStatus status3 = (ArrivalStatus) value3; // int casted to enum

int value4 = (int) status3; // enum casted to int
```

## Using `IsDefined()` Before Converting
using the `IsDefined` method prevents assigning a value that is not a member of the enum:
```cs
if (Enum.IsDefined(typeof(ArrivalStatus), 5)) // returns False
```

## Converting an Enum Value to its Underlying Type
```cs
ArrivalStatus foo = ArrivalStatus.Early;

var number = Convert.ChangeType(foo, Enum.GetUnderlyingType(typeof(ArrivalStatus))); // number is 1.
```

## Parsing Enumeration Values (string -> enum)
```cs
string name = "Early";

if (Enum.TryParse<ArrivalStatus>(name, out ArrivalStatus bar)) 
{ // True
  // …
}
```

# Iterating Enumeration Members
First, get a string array of the names of the enum members:
```cs
string[] names = Enum.GetNames(typeof(ArrivalStatus));

// Next, call Parse to convert the string to its enum value:
foreach (var name in names) 
{
  ArrivalStatus status = (ArrivalStatus) Enum.Parse(typeof(ArrivalStatus), name);
}
```

# Iterating Enumeration Values
Like above, except call `Enum.GetValues` to get an array of the enum's underlying values.

# Flags Attribute
The Flags attribute allows an enum object to include multiple members of the enum.
- Note: Requires defining enum constants in powers of 2.
- Note: Do not define a negative number as a flag.

```cs
[Flags] public enum Pets { None=0, Dog=1, Cat=2, Bird=4, Rodent=8 };

Pets familyPets = Pets.Dog | Pets.Cat;

familyPets.HasFlag(Pets.Dog); // True.
```

# Enum Extension Methods
Enums are defined by language structures so you cannot define custom methods for an enumeration type. However, you can use extension methods:

```cs
public enum Grades { F = 0, D = 1, C = 2, B = 3, A = 4 };

public static class Extensions 
{
  public static Grades minPassingGrade = Grades.D;

  public static bool Passing(this Grades grade) { return grade >= minPassing; }
}

Grades g1 = Grades.F;
g1.Passing() // False.
```
