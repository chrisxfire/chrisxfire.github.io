---
title: "notes > dotnet > classes > methods > extension methods"
date: 2022-02-26T21:38:42-0700
draft: true
---
# Extension Methods
Extension methods extend existing types without creating a new derived type.
They are static methods, but they are called as if they were instance methods on the extended type.
Extension methods can also extend types that are sealed.

## Binding
An extension method with the same name and signature as an interface or class method will never be called.
The compiler will always bind to the interface or class method when there is a conflict.

# Creating
To make extensions methods, make two changes:
namespace MyExtensions;

public static class StringExtensions { // The class must be static.
public static int WordCount(this string str) { // The method must be static; the type must be prefixed this.
return str.Split(new char[] { ' ', '.', '?' }, StringSplitOptions.RemoveEmptyEntries).Length;
}
}

# Scoping
Extension methods are brought into scope at the namespace level.

Bring the WordCount extension into scope:
using MyExtensions;

# Invoking
Once in scope, extension methods can be invoked like an instance method:
string s = "Hello, world";
int i = s.WordCount();

or, like a static method:
int i = MyExtensions.WordCount(s);

# Common Usage Patterns
1.  Extending System.Collections.Generic.IEnumerable<T> creates extension methods that can be used on any collection that implements IEnumerable<T>.
2.  When using an Onion Architecture, extension methods can be used to add functionality that is specific to each application layer without loading theobject down with methods not needed in other layers.
3.  Extend existing .NET or CLR types.
    1.  Note: When extending a struct type, add the ref modifier to the first argument of the extension method. This allows the extension method to change the state of the struct being extended.

## LINQ Extensions
To bring the LINQ standard query operators into scope:
using System.Linq;

Now, any type that implements IEnumerable<T> has instance methods GroupBy, OrderBy, Average, and more.

# Extending an Enum
namespace EnumExtension;

public static class Extensions {
public static Grades minPassing = Grades.D;
public static bool Passing(this Grades grade) { return grade >= minPassing; }

}

public enum Grades { F=0; D=1; C=2; B=3; A=4 };
