---
title: notes > dotnet > types > properties
date: 2021-11-06T11:25:46-0600
draft: false
---
# Properties
Properties are methods that act like Fields that allow for getting and setting its value.
- They are used in place of fields when the value they contain must be calculated or guarded.
- To the user of a property, they appear as a field.
- Unlike fields, they are implemented with get/set accessors that define the statements executed when the property is accessed or assigned.
- Properties cannot be passed as ref or out parameters.

# Creating
Properties with `get` accessors only are read-only. Properties with both `get` and `set` are read-write.
Write-only properties are rare and generally used to restrict access to sensitive data.

```cs
// This class has a hidden, parameterless constructor.
public class Person 
{
    // This is a backing field:
    private string _firstname;
    private string _location;

    // This is a manual read-only property:
    public string Firstname 
    {
        get { return _firstname; }

        // The *value* parameter holds the value passed to the constructor during instantiation.
        // It's type is the type of the property:
        set { _firstname = value; }
    }

    // Auto-implemented Properties  
    // If one accessor is auto, both must be. The compiler adds a hidden backing field:
    public string Lastname { get; set; } // The compiler adds *readonly* to the get accessor.

    // This is an auto read-only property. It will be set to the default value for its type.
    public int Age { get; }

    // Auto-implemented properties can be intialized to a default value:
    public string FavoriteColor { get; set; } = "Red";

    // This property uses expression body syntax definitions:
    public string Location 
    {
        get => _location;
        set => _location = value;
    }
}
```

# Validation
Validation is one of the key uses of properties:
```cs
public class Person 
{
    private string _firstName;

    public string FirstName 
    {
        get => _firstName;
        // Set accessors must return void, so errors must be reported by throwing an exception:
        set => _firstName = (!string.IsNullOrWhiteSpace(value)) ? value : throw new ArgumentException("First name must not be blank");
    }
}
```

# Read-only vs. Init-only
Read-only properties can only be set in their constructor, but not via object-initializer syntax:
```cs
public string FirstName { get; }
// Illegal: Person p = new Person() { FirstName = "Jane" };
// Legal: Person p = new Person("Jane");

// Init-only properties are read-only propertis that support object-initializer syntax:
public string FirstName { get; init; }
// Legal: Person p = new Person() { FirstName = "Jane" };
```

# Computed Properties
Properties can return computed values. They must be constructed carefully:
```cs
public class Person 
{
    private string _firstName;
    private string _lastName;
    private string _fullName;

    public string FirstName 
    {
        get => _firstName;
        // Each time FirstName is set, also set _fullName to null, which forces it to be computed again:
        set 
        {
            _firstName = value;
            _fullName = null;
        }
    }
    public string LastName 
    {
        get => _lastName;
        // Same as with FirstName:
        set 
        {
            _lastName = value;
            _fullName = null;
        }
    }
    public string FullName 
    {
        get 
        {
            if (_fullName is null) // If it's null, set it; if not, return it:
                _fullName = $"{FirstName} {LastName}";
            
            return _fullName;
        }
    }
}
```

# Using Properties
```cs
MyList<string> names = new MyList<string>();
names.Capacity = 100; // Invokes set accessor
int i = names.Count; // Invokes get accessor
int j = names.Capacity; // Invokes get accessor
```

# Property Modifiers
When a property is modified, so are its accessors.  
Properties can be static or instance.  
Properties can be modified with `public`, `private`, `protected`, `internal`, `protected internal`, or `private protected`.  

Other modifiers:
- `virtual` - The property can be overridden in a derived class.
- `override` - Overrides the implementation of a virtual property from the base class.
- `sealed` - A property overriding a virtual property can be sealed so that it is no longer virtual in further
derived classes.
- `abstract` - See below.
- `required` The compiler will throw an error if the property is not set to a value when it is instantiated.

# Accessors (set vs init vs private set)
- `set` - property can be set within this type and consumers of the type.
- `private set` - property can only be set within this type, but immutable to consumers.
  - Cannot use an object initializer. Must use a constructor or factory method.
- `init` - property can only be set during instantiation; supports object-initializer syntax.
- `required` - property must be set when an object of the type is created.

# Attributes
## Required Members
```cs
public class Person 
{
    public Person() { }

    [SetsRequiredMembers] // Notifies compiler that this constructor sets all required members.
    public Person(string firstName) => FirstName = firstName;

    public required string FirstName { get; init; }
}
```

## Field Specifiers
A field specifier indicates that the attribute applies to the backing field of an auto-implemented property:
```cs
[field:NonSerialized]
public int Id { get; set; }
```

# Accessor Access Modifiers
Accessors can have access modifiers…
- …but only if the property has both *get* and *set* accessors…
- …and only one of the two can have an access modifier.
- If the property has an override modifier, the accessor modifier must match the accessor of the overridden accessor.
- The accessibility level on the accessor must be more restrictive than that of the property itself.

Use the `private` modifier so that an accessor can only be used by methods in the class:
```cs
public string Firstname { get; private set; } // Firstname can only be changed by other methods in the class.
```

# Abstract Properties
An abstract property does not provide an implementation of its accessors. This is done by the derived classes:
```cs
public abstract class Shape 
{
    private string name;

    public Shape(string s) 
    {
        Id = s; // Calls the set accessor of the Id property.
    }

    public string Id 
    {
        get => name;
        set => name = value;
    }

    // This abstract property must be implemented (overridden) in a derived class.
    public abstract double Area { get; }
}

public class Square : Shape 
{
    public Square(int side, string id) : base(id) 
    {
        this.side = side;
    }

    // Overrides abstract property Area from Shape to implement it.
    public override double Area
    { 
        get { return side * side; }
    }
}
```

# Properties in Interfaces
Interface properties do not have a body.
- Declaring the accessors without a body does not declare an auto property like it does in classes and structs.
- Interface properties cannot have accessor access modifiers.

```cs
public interface ISampleInterface 
{
    string Name { get; set; } // The accessors must be implemented in the deriving type.
}
```

# `INotifyPropertyChanged`
When the value of a property changes, the object raises the `INotifyPropertyChanged.PropertyChanged` event. Here's how it's implemented:
```cs
public class Person : INotifyPropertyChanged 
{
    private string _firstName;

    public string FirstName 
    {
        get => _firstName;
        set 
        {
            if (string.IsNullOrWhiteSpace(value))
                throw new ArgumentException("…");
            
            if (value != _firstName) 
            {
                _firstName = value;

                PropertyChanged?.Invoke(this, new PropertyChangedEventArgs(nameof(FirstName)));
            }
        }
    }

    public event PropertyChangedEventHandler PropertyChanged;
}
```
