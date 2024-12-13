---
title: collection expressions
date: 2023-10-15T00:00:00-06:00
draft: false
weight: 1
---

# Overview [[Documentation](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/collection-expressions)]  
> [!IMPORTANT]
> Availability: C# 12

Use *collection expressions* to create common collection values. This syntax can be assigned to many different collection types. It contains
a sequence of elements between `[` and `]`.

# Usage
Collection expressions can be used across many constructs:
```cs
// In a variable declaration:
Span<string> weekDays = [ "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" ];
```
```cs
// To initialize a private field:
private static readonly ImmutableArray<string> _months = [ "Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec" ];

// To initialize a property with an expression body:
public IEnumerable<int> MaxDays => [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 ];

public int Sum(IEnumerable<int> values) => values.Sum();

public void Example()
{
    // As a parameter:
    int sum = Sum([1, 2, 3, 4, 5]);
}
```

You can also use variables as the elements of the collection expression:
```cs
string hydrogen = "H";
string helium = "He";
string lithium = "Li";
string beryllium = "Be";
string boron = "B";
string carbon = "C";
string nitrogen = "N";
string oxygen = "O";
string fluorine = "F";
string neon = "Ne";
string[] elements = [ hydrogen, helium, lithium, beryllium, boron, carbon, nitrogen, oxygen, fluorine, neon ];
```

# Spread Elements
A *spread element* `..` can be used to *inline* collection values in a collection expression:
```cs
string[] vowels = [ "a", "e", "i", "o", "u" ];
string[] consonants = [ "b", "c", "d", "f", "g", "h", "j", "k", "l", "m",
                        "n", "p", "q", "r", "s", "t", "v", "w", "x", "z" ];
string[] alphabet = [ ..vowels, ..consonants, "y" ];
```

# Restrictions
Collection expressions cannot be used:
* Where a compile-time constant is expected
* As the default value for a method argument

# Creating Collection Types that Support Collection Expressions
1. Write a `Create` method that:
   1. Returns an object of the collection type
   2. Takes a single parameter of the element type
2. Add the `[CollectionBuilder]` attribute to the collection type

Consider this `LineBuffer` type:
```cs {hl_lines=2}
// #2: The attribute added to the collection type and providing the name of the Create method as a parameter:
[CollectionBuilder(typeof(LineBufferBuilder), "Create")]
public class LineBuffer : IEnumerable<char>
{
    private readonly char[] _buffer = new char[80];

    public LineBuffer(ReadOnlySpan<char> buffer)
    {
        int number = (_buffer.Length < buffer.Length) ? _buffer.Length : buffer.Length;
        for (int i = 0; i < number; i++)
        {
            _buffer[i] = buffer[i];
        }
    }

    public IEnumerator<char> GetEnumerator() => _buffer.AsEnumerable<char>().GetEnumerator();
    IEnumerator IEnumerable.GetEnumerator() => _buffer.GetEnumerator();

    // ...
}
```

```cs {hl_lines=6}
internal static class LineBufferBuilder
{
    // #1: A Create() method that:
        // #1.1: returns an object of the collection type (LineBuffer)
        // #1.2: takes a single parameter of the element type (ReadOnlySpan<char>) 
    internal static LineBuffer Create(ReadOnlySpan<char> values) => new LineBuffer(values);
}
```

# Converting Collection Expressions to Collection Types
See https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/collection-expressions#conversions