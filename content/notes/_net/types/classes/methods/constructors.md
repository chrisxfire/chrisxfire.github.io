---
title: constructors
date: 2021-11-06T11:25:27-0600
draft: false
weight: 1
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
public Person() : this("Doe", "John") { } // Calls Person(*lastName*, *firstName*)
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
