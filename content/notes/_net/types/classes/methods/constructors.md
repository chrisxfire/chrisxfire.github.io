---
title: constructors
date: 2021-11-06T11:25:27-0600
draft: false
weight: 1
tags:
 - kb/dotnet/types/classes/methods/constructors
---

# [Constructors](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/constructors)
Whenever a Class or Struct is created, its *constructor* is called.

# Instance Constructors
```cs
public class Person 
{
    private string Last;
    private string First;

    // Instance constructors initialize an instance of a class and are not inherited in derived classes.
    // Constructors have the same name as the class and are usually at the bottom of the class:
    public Person(string lastName, string firstName) 
    {
        Last = lastName;
        First = firstName;
    }
}
```

Constructors do not use `return` statements.

# Invoking
Constructors are invoked with `new`:
```cs
Person p1 = new Person("smith", "eli") // Instantiate a Person instance.
```

# Parameterless Constructors
Parameterless constructors can be explicitly implemented.  
They are auto-implemented on classes that have no other constructor.  
They can call parameterized constructors with default values, if desired:  
```cs
public Person() : this("Doe", "John") { } // Calls Person(lastName, firstName)
```

Structs cannot contain explicit parameterless constructors because one is auto-implemented by the compiler. For example:
```cs
int i = new int(); // Parameterless constructor used to invoke an int and initialize it to its default value.
```

# Base Class Constructors
Derived class constructors can call the constructor of the base class:
```cs
public class Employee : Person 
{
    public string EmployeeID;

    public Employee(string f, string l, string id) // This constructor will run second.
    : base(f, l) // This constructor will run first.
    {
        this.EmployeeID = id;
    }
}
```

# [Static Constructors](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/static-constructors)
Static constructors initialize a class itself (not an instance of the class).  
They initialize static members of the class or struct.  
They are called automatically, once, immediately before any static fields are accessed.  
They are created with the static prefix.  
They are parameterless.  

# [Private Constructors](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/private-constructors)
Private constructors are generally used in classes that only have static members.  
- If this is the case, consider making the whole class static.
Classes with private constructors cannot be instantiated.  
They are created with the private prefix and are empty:
```cs
class Employee 
{
    private Employee() { }
}
```

# [Copy Constructors](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor)
Copy constructors are used to copy an object, including the values of its properties, to a new instance of that type.
In C#, records provide a copy constructor for objects. Classes do not, so one must be written:
```cs
class Person 
{
    // "Regular" (instance) constructor:
    public Person(string name, int age) 
    {
        Name = name;
        Age = age;
    }

    // Copy constructor:
    public Person(Person otherPerson) 
    {
        Name = otherPerson.Name;
        Age = otherPerson.Age;
    }

    // Another example of a copy constructor; this one calls the instance constructor to copy the object:
    public Person(person otherPerson) : this(otherPerson.Name, otherPerson.Age) { }

    // Properties:
    public int Age { get; set; }
    public string Name { get; set; }

    public string Details() 
    {
        return $"{Name} is {Age}";
    }
}
```

# Async Constructors
It is impossible to create an async constructor. Instead, consider this pattern:
```cs
public class ViewModel
{
    public ObservableCollection<TData> Data { get; set; }

    // Static async method that behave like a constructor
    async public static Task<ViewModel> BuildViewModelAsync()
    {
        ObservableCollection<TData> tmpData = await GetDataTask();
        return new ViewModel(tmpData);
    }

    // Private constructor called by the async method
    private ViewModel(ObservableCollection<TData> Data)
    {
        this.Data = Data;
    }
}

// Objects are created like this:
ViewModel vm = await ViewModel.BuildViewModelAsync();
```

# [Primary Constructors](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/instance-constructors#primary-constructors)
> [!IMPORTANT] Availability: .NET 8 with C# 12

Primary constructors are constructors with parameters added. They indicate that these parameters are necessary for any instance of the type.
A primary constructor's parameters are available anywhere in the type definition. 

> [!IMPORTANT] 
> Primary constructor parameters are, in fact, parameters—not members—of the type.

Rules:
- They may not be stored if they are not needed.
- They are not members, so they cannot be accessed via the `this` keyword.
- They can be assigned to.
- They do not become properties, except in record types.
- Every other constructor of a class **must** call the primary constructor through a `this()` constructor invocation.


Primary constructors are available to classes, structs, and records.

## Implementation Details
- In any `class` type, including `record class`, the implicit parameterless constructor is <r>not</r> emitted when a primary constructor is presented.
- In any `struct` type, including `record struct`:
  - the implicit parameterless construct is <g>always</g> emitted
  - all fields are always initialized to the 0-bit pattern
- In and only in a `record class` or `record struct`, the compiled synthesizes a public property with the same name as the primary constructor parameter. 
- In and only in a `record class`, if a primary constructor parameter uses the same name as a base primary constructor, that property is a public property of the base `record class` type.

> [!TIP]
> More information: https://learn.microsoft.com/en-us/dotnet/csharp/whats-new/tutorials/primary-constructors

## Common Uses
1. As an argument to a `base()` constructor invocation.
2. To initialize a member field or property.
3. Referencing the constructor parameter in an instance member.
4. Specify parameters for dependency injection.

## Example: Basic
Consider this type:
```cs
public class NamedItem(string name)
{
    public string Name => name;
}
```

This `Widget` type that derives from `NamedItem` must have a `this()` constructor invocation:
```cs
// name isn't captured in Widget.
// width, height, and depth are captured as private fields
public class Widget(string name, int width, int height, int depth) : NamedItem(name)
{
    public Widget() : this("N/A", 1,1,1) {} // unnamed unit cube

    public int WidthInCM => width;
    public int HeightInCM => height;
    public int DepthInCM => depth;

    public int Volume => width * height * depth;
}
```

## Example: Initializing a Property
Two readonly properties are computed from primary constructor parameters:
```cs
public readonly struct Distance(double dx, double dy)
{
    public readonly double Magnitude { get; } = Math.Sqrt(dx * dx + dy * dy);
    public readonly double Direction { get; } = Math.Atan2(dy, dx);
}
```

This would be equivalent to:
```cs
public readonly struct Distance
{
    public readonly double Magnitude { get; }

    public readonly double Direction { get; }

    public Distance(double dx, double dy)
    {
        Magnitude = Math.Sqrt(dx * dx + dy * dy);
        Direction = Math.Atan2(dy, dx);
    }
}
```

## Example: Dependency Injection
This controller's primary constructor indicates the parameters needed for its class:
```cs
public interface IService
{
    Distance GetDistance();
}

public class ExampleController(IService service) : ControllerBase
{
    [HttpGet]
    public ActionResult<Distance> Get()
    {
        return service.GetDistance();
    }
}
```