---
title: notes > code > .net > types > reference types > generics > generics
date: 2021-11-07T19:58:42-0700
draft: false
---
# Generics
Generics are for types and methods.  
They allow you to pass *types* as *parameters*, similar to how you can pass objects as parameters.  
They defer the specification of one or more types until the class/method has been instantiated.  

A generic class cannot be used as-is because it is not a type; it is a blueprint for a type.  
Client code must declare and initialize a constructed type by specifying a type argument in the \<brackets\>.  

# Creating
```cs
public class GenericList<T> 
{
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