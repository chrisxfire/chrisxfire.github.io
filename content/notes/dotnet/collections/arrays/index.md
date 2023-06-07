---
title: notes > dotnet > collections > arrays
date: 2021-11-06T11:43:18-0600
draft: falsee
---
# [Arrays](https://docs.microsoft.com/en-us/dotnet/api/system.array?view=net-6.0)
- Use arrays when working with a fixed number of strongly typed items.
- Arrays are objects that have properties and methods in the [System.Array](https://docs.microsoft.com/en-us/dotnet/api/system.array?view=net-6.0) class.
- An array's length (the number of elements it has) and its dimensions are set when the array instance is created and cannot be changed.
- Arrays implement IList and IEnumerable. Single-dimensional arrays also implement IList<T> and IEnumerable<T>.

# Declaring
Declare a single-dimensional array of 5 integers:
```cs
int[1] a1 = new int[5];
// Or declare an array variable without creating it…
int[] a2;
// …and then use the new operator when assigning a new array to this variable:
a2 = new int[] { 1, 3, 5, 7, 9 };
```

# Initializing
Declare and initialize a single-dimensional array of 5 integers:
```cs
int[] a2 = new int[] { 1, 3, 5, 7, 9 };
// or
int[] a3 = { 1, 3, 5, 7, 9 };
```
# Multidimensional Arrays
Multidimensional arrays are created with the syntax: new T[rows, columns]
Declare a 2D array:
```cs
int[,] twoDimArray = new int[2, 3];
```

Declare and initialize:
```cs
int[,] twodimArrayA = new int[,] { { 1, 2, 3 }, { 4, 5, 6 } };
// or
int[,] twoDimArrayB = new int[3,3] { { 1, 2, 3 }, { 4, 5, 6 } };
// or
int[,] twoDimArrayC = { { 1, 2, 3 }, { 4, 5, 6 } };

// Or a 3D array: X, Y, Z
int[,,] threeDimArray = new int [4, 2, 3];
```
# Jagged Arrays
A jagged array is an array of arrays.
Its elements are always reference types initialized to null.

## Declare
Declare a an array that has 3 elements, each of which is a 1D array of integers of unspecified length:
```cs
int[][] jArray = new int[3][];
```
## Initialize
Initialize the elements:
```cs
jArray[0] = new int[3];
jArray[1] = new int[5];
jArray[2] = new int[7];

// Or, initialize the elements and fill them with values:
jArray[0] = new int[] { 2, 4, 6 };
jArray[1] = new int[] { 1, 3, 5, 7, 9 };
jArray[2] = new int[] { 10, 20, 30, 40, 50, 60, 70 };
```

## Declare & Initialize
Declare, initialize, and fill the array elements all at once:
```cs
int[][] jArray2 = new int[][] 
{
    new int[] { 2, 4, 6 },
    new int[] { 1, 3, 5, 7, 9 },
    new int[] { 10, 20, 30, 40, 50, 60, 70 }
}

// Or, use this shorthand form:
int[][] jArray3 = 
{
    new int[] { 2, 4, 6 },
    new int[] { 1, 3, 5, 7, 9 },
    new int[] { 10, 20, 30, 40, 50, 60, 70 }
}
```
## Assign Values
Assign the first array's (`[0]`) second element (`[1]`) the value 77:
```cs
jArray3[0][1] = 77;
```
# Accessing
```cs
a[n]
a[^n] // Return the nth item from the end of the array.
a[m..n] // Return the mth item to the nth item, exclusive.
```
# Implicitly Typed Arrays
Implicity-typed arrays are usually used in query expressions together with anonymous types and object and collection initializers.

Single-dimension, implicitly-typed:
```cs
var a = new[] { 1, 10, 100, 1000 }; // Implicitly-typed to int[].
var b = new[] { "hello", null, "world" }; // Implicitly-typed to string.

// Single-dimension, jagged, implicitly-typed:
var c = new[] 
{
    new[] { 1, 2, 3, 4 },
    new[] { 5, 6, 7, 8 }
};
```

# Anonymous Types that Contain Arrays
Here, contacts is an implicitly-typed array of anonymous types, each of which contains an array named PhoneNumbers:
```cs
var contacts = new[] 
{
    new 
    {
        Name = "Jen",
        PhoneNumbers = new[] { "321-4119", "867-5309" }
    },
    new 
    {
        Name = "Chris",
        PhoneNumbers = new[] { "321-4270", "867-5309" }
    }
};
```
# Properties
`.Length` The number of elements in the array.

# Static Methods
## Manipulating
```cs
Array.Clear(array, s, n) // Clear n elements from array starting at index s.
Array.Resize(ref array, n) // Resize array to size n.
// - When shrinking, this removes elements from the end of the array toward the beginning.
Array.Reverse(array)
```
## Searching
```cs
Array.BinarySearch(array, elem) // Searches array for elem. Returns the index of elem if found
or -1 if not found.
Array.Find(array, predicate match) // Searches array for match and returns the first match.
// Example: Array.Find(array, element => element == 3);
Array.Findall(array, predicate match) // Searches array for match and returns an array of all matches.
Array.FindLast(array, predicate match) // Searches array for match and returns the last match.
```

## Sorting
`Array.Sort(array)`

# Iterating
Use foreach:
```cs
string[] names = { "eli", "noah", "jen" };
foreach (string name in names) { … }
```
When iterating multidimensional arrays, they are traversed such that the indices of the rightmost dimension are increased first, then the next left dimension, and so on:
```cs
int[,] numbers2D = new int[3, 2] { { 9, 99 }, { 3, 33 }, { 5, 55 } };

foreach (int i in numbers2D)
System.Console.Write($"{i}");

// Output: 9 99 3 33 5 55
```
