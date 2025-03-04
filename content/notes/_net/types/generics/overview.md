---
title: overview
date: 2021-11-07T19:58:42-0700
draft: false
weight: -1
---

# generics
Generics are classes, structures, interfaces and methods that have placeholders (*type parameters*) for one or more of the types that they store or use.  They allow you to pass *types* as *parameters*, similar to how you can pass objects as parameters.  They defer the specification of one or more types until the class/method has been instantiated (a *constructed generic class*).

A generic class cannot be used as-is because it is not a type; it is a blueprint for a type.  
Client code must declare and initialize a constructed type by specifying a type argument in the \<brackets\>.  

# creating
```cs
// A generic class:
public class GenericList<T> 
{
    // A generic method:
    public void Add(T input) { }
}

class TestGenericList 
{
    private class ExampleClass { }

    static void Main() 
    {
        // Declare a list of type int:
        GenericList<int> list1 = new GenericList<int>();
        list1.Add(1);

        // Declare a list of type string:
        GenericList<string> list2 = new GenericList<string>();
        list2.Add("");

        // Declare a list of type ExampleClass:
        GenericList<ExampleClass> list3 = new GenericList<ExampleClass>();
        list3.Add(new ExampleClass());
    }
}
```

Generic classes define *type parameters*:
```cs
public class Pair<TFirst, TSecond>// TFirst and TSecond are the type parameters of Pair.
{
    public TFirst First { get; }
    public TSecond Second { get; }
    public Pair(TFirst first, TSecond second) => (First, Second) = (first, second);
}
```

When generic classes are used, arguments must be provided for each parameter:
```cs
var pair = new Pair<int, string>(1, "two");
int i = pair.First; // TFirst int
string s = pair.Second; // TSecond string
```

# generic attributes
> [!IMPORTANT]
> Availability: C# 11  

To create a generic attribute, create a class whose base class is `Attribute`:  

```cs
// C# 11 feature:
public class GenericAttribute<T> : Attribute { }
```

Use the generic attribute by specifying the type parameter:
```cs
[GenericAttribute<string>()]
public string Method() => default;
```

# considerations
- Generic methods can appear on both generic and non-generic types.  Just because a type is generic does not mean its methods are.
  - A method is generic only if it has its own list of type parameters.
- Generic type safety is enforced at *compile time*.
- [Generic collection](../../collections/generic) types generally perform better for storing and manipulating value types because they do not need to [box](../../../fundamentals/boxing-and-unboxing/) the value types.
- [Enumerations](../../value-types/enums) cannot have generic type parameters.
- The CLR considers a type that is nested in a generic type to be generic even if it does not have generic type parameters of its own.
  - To create an instance of such a type, you must specify type arguments for all enclosing generic types.

# variance
As it pertains to generics, these concepts apply to the generic type parameter of the generic type.
- Documentation: https://learn.microsoft.com/en-us/dotnet/standard/generics/covariance-and-contravariance

## covariance
Enables the use of a more derived (more specific) type than originally specified.
- An instance of `IEnumerable<Dog>` can be assigned to a variable of type `IEnumerable<Animal>`.

### defining
A covariant type parameter is marked with the `out` keyword.

## contravariance
Enables the use of a less derived (less specific) type than originally specified.
- An instance of `IEnumerable<Animal>` can be assigned to a variable of type `IEnumerable<Dog>`.

### defining
A contravariant type parameter is marked with the `in` keyword.

## invariance
Only the type originally specified can be used.
- An instance of `IEnumerable<Dog>` <u>cannot</u> be assigned to a variable of type `IEnumerable<Animal>` or vice-versa.

## summary table
| Variance      | Use as interface method return value? | Use as delegate return type? | Use as interface method type constraint? |
| ------------- | ------------------------------------- | ---------------------------- | ---------------------------------------- |
| Covariant     | Yes                                   | Yes                          | No                                       |
| Contravariant | Yes                                   | Yes                          | Yes                                      |

## considerations
- Variant type parameters are restricted to generic interface and generic delegate types
  - These types can also have both covariant and contravariant type parameters
- Variance applies only to reference types: if you specify a value type for a variant type parameter, that type parameter is invariant for the resulting constructed type.
- Covariant return types are supported (C# 9). 
  - An overriding method can declare a more derived return type of the method it overrides. 
  - An overriding, read-only property can declare a more derived type.

Generally:
- A covariant type parameter can be used as the return type of a delegate.
- A contravariant type parameter can be used as a parameter type.

For generic interfaces:
- Covariant type parameters can be used as the return types of the interface's methods.
- Contravariant type parameters can be used as the parameter types of the interface's methods.
