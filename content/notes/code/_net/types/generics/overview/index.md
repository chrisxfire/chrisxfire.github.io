---
title: notes > code > .net > types > generics > overview
date: 2021-11-07T19:58:42-0700
draft: false
weight: -1
---

# Generics
Generics are classes, structures, interfaces and methods that have placeholders (*type parameters*) for one or more of the types that they store or use.  They allow you to pass *types* as *parameters*, similar to how you can pass objects as parameters.  They defer the specification of one or more types until the class/method has been instantiated (a *constructed generic class*).

A generic class cannot be used as-is because it is not a type; it is a blueprint for a type.  
Client code must declare and initialize a constructed type by specifying a type argument in the \<brackets\>.  

# Creating
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

# Considerations
- Generic methods can appear on both generic and nongeneric types.  Just because a type is generic does not mean its methods are.
  - A method is generic only if it has its own list of type parameters.
- Generic type safety is enforced at *compile time*.
- [Generic collection](../../../../collections/generic/) types generally perform better for storing and manipulating value types because they do not need to [box](../../../../fundamentals/boxing-and-unboxing/index.md) the value types.
- [Enumerations](../../../value-types/enums/index.md) cannot have generic type parameters.
- The CLR considers a type that is nested in a generic type to be generic even if it does not have generic type parameters of its own.
  - To create an instance of such a type, you must specify type arguments for all enclosing generic types.
