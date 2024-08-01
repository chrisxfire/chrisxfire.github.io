---
title: records
date: 2021-11-07T19:30:56-0700
draft: false
weight: 1
---
# Records
Records can be `record class`es or `record struct`s.

## Use When
- You need a data model that depends on value equality
- You need a type whose objects are immutable

## Do Not Use
- As entity types in Entity Framework Core.

# Positional Syntax
*Positional syntax* will automatically declare properties, a constructor, and a deconstructor:
```cs
public record Person(string FirstName, string LastName);

public static void Main()
{
    Person person = new("Nancy", "Davolio");
    Console.WriteLine(person);
    // output: Person { FirstName = Nancy, LastName = Davolio }
}
```

# Record Class
Record classes, a reference type (defaults to `record class` if `class` or `struct` not specified):
```cs
public record Person 
{
    public string FirstName { get; init; } = default!
    public string LastName { get; init; } = default!
};
```

## Characteristics
- Allocation: Heap
- Equality: Reference
- Semantics: Reference
- Inheritance: Single (from another record only)
- Mutability: Mutable, but generally treated immutable

A *positional* `record class` declares init-only properties, making them immutable.

# Record Struct
Record struct, a value type:
```cs
public record struct Point 
{
    public double X { get; set; }
    public double Y { get; set; }
    public double Z { get; set; }
}
```

## Characteristics
- Allocation: Stack
- Equality: Value
- Semantics: Value
- Inheritance: None (sealed)
- Mutability: Mutable, but generally treated immutable

A *positional* `record struct` declares read-write properties, making them mutable.

# Readonly Record Struct

A *positional* `readonly record struct` declares init-only properties, making them immutable.

## Example
```cs
public record Person(string FirstName, string LastName);

public static void Main()
{
    Person person = new("Nancy", "Davolio");
    Console.WriteLine(person);
    // output: Person { FirstName = Nancy, LastName = Davolio }
}
```

# Equality
For `record class` types, two objects are equal if they refer to the same object in memory.
For `record struct` and `readonly record struct` types, two objects are equal if they are of the same type and store the same values.
- This is the same as equality for a `struct` type.

# Adding Targets to Attributes Applied to Records
The `property` target applies the attribute to the compiler-generated auto-property.  
The `field` target applies the attribute to the field.  
The `param` target applies the attribute to a parameter.  

```cs
public record Person(
    [property: JsonPropertyName("firstName")] string FirstName,
    [property: JsonPropertyName("lastName")] string LastName)
{
    public string PhoneNumber { get; init; }
}
```

# Non-destructive Mutation
By using the `with` keyword, a new record instance is created with specified properties and fields modified:
```cs
person p1 = new("Super", "Man") { PhoneNumber = 5555555555 };
person p2 = p1 with { FirstName = "Bat" };
```

# Built-in Formatting for Display
Records have a compiler-generated `ToString` method that displays the names and values of public properties and fields.
It uses this format: `record-type-name { property-name = value, property-name = value, … }`  

An implementation of `ToString` may include the `sealed` modifier, which prevents the compiler from synthesizing a `ToString` implementation for any derived records. This creates a consistent string representation throughout a hierarchy of record types.


# Examples
```cs
// You can give a record a constructor:
public record class ImmutableAnimal 
{
    public string Name { get; init; }
    public string Species { get; init; }

    public ImmutableAnimal(string name, string species) 
    {
        Name = name;
        Species = species;
    }

    // And a deconstructor:
    public void Deconstruct(out string name, out string species) 
    {
        name = Name;
        species = Species;
    }
}
```
