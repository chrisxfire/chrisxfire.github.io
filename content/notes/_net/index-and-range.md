---
title: index and range
date: 2022-01-09T19:17:18-0700
draft: false
weight: 1
tags:
 - kb/dotnet/index
 - kb/dotnet/range
---

# [overview](https://learn.microsoft.com/en-us/dotnet/csharp/tutorials/ranges-indexes)
Index and range operators can be used with any type that *countable*. A type is countable if it has an `int` property named `Count` or `Length` and a `get` accessor. 

# [index](https://learn.microsoft.com/en-us/dotnet/api/system.index?view=net-9.0)
`System.Index` represents an index into a sequence. 

Normally, the index is an integer passed to the indexer of an array:
```cs
int index = 3;
Person p = people[index]; // The fourth Person in the array.
```
The `Index` value type can identify position.

## creating
This index counts from the start:
```cs
Index i1 = new(value: 3);
```
or
```cs
Index i2 = 3;
```
This index counts from the end:
```cs
Index i3 = new(value: 7, fromEnd: true);
```
or
```cs
Index i4 = ^7
```

## [index from end operator (`^`)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/member-access-operators#index-from-end-operator-)
Indicates the element position from the end of a sequence. `^n` is of type `System.Index`:
- For a sequence of `length`, `^n` points to the element at `length - n`
- `^1` points to the last element of a sequence
- `^length` points to the first element of a sequence

Examples:
```cs
int[] xs = [0, 10, 20, 30, 40];
int last = xs[^1];
Console.WriteLine(last);  // output: 40

List<string> lines = ["one", "two", "three", "four"];
string prelast = lines[^2];
Console.WriteLine(prelast);  // output: three

string word = "Twenty";
Index toFirst = ^word.Length;
char first = word[toFirst];
Console.WriteLine(first);  // output: T
```

# [range](https://learn.microsoft.com/en-us/dotnet/api/system.range?view=net-9.0)
The `Range` value type uses `Index` values to indicate the start and end of its range.
```cs
Range r1 = new(start: new Index(3), end: new Index(7));
Range r2 = new(start: 3, end: 7);
Range r3 = 3..7;
Range r4 = Range.StartAt(3); // from index 3 to end
Range r5 = 3..; // same
Range r6 = Range.EndAt(3); // from index 0 to index 3
Range r7 = ..3; // same
```

## [range operator (`..`)](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/operators/member-access-operators#range-operator-)
The range operators specifies the start and end of a range of indices as its operands. An expression `a..b` is of type `System.Range`:
- `a` is an *inclusive* start of a range
- `b` is an *exclusive* end of a range

Examples:
```cs
int[] numbers = [0, 10, 20, 30, 40, 50];
int start = 1;
int amountToTake = 3;
int[] subset = numbers[start..(start + amountToTake)];
Display(subset);  // output: 10 20 30

int margin = 1;
int[] inner = numbers[margin..^margin];
Display(inner);  // output: 10 20 30 40

string line = "one two three";
int amountToTakeFromEnd = 5;
Range endIndices = ^amountToTakeFromEnd..^0;
string end = line[endIndices];
Console.WriteLine(end);  // output: three

void Display<T>(IEnumerable<T> xs) => Console.WriteLine(string.Join(" ", xs));
```

Ranges can be open-ended:
- `a..` is equivalent to `a..^0`
- `..b` is equivalent to `0..b`
- `..` is equivalent to `0..^0`

```cs
int[] numbers = [0, 10, 20, 30, 40, 50];
int amountToDrop = numbers.Length / 2;

int[] rightHalf = numbers[amountToDrop..];
Display(rightHalf);  // output: 30 40 50

int[] leftHalf = numbers[..^amountToDrop];
Display(leftHalf);  // output: 0 10 20

int[] all = numbers[..];
Display(all);  // output: 0 10 20 30 40 50

void Display<T>(IEnumerable<T> xs) => Console.WriteLine(string.Join(" ", xs));
```

## range indices and arrays
When an array is sliced, a new array (rather than a reference to the sliced array) is created.

# index and range operator examples
```cs
int[] oneThroughTen =
[
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10
];

Write(oneThroughTen, ..);
Write(oneThroughTen, ..3);
Write(oneThroughTen, 2..);
Write(oneThroughTen, 3..5);
Write(oneThroughTen, ^2..);
Write(oneThroughTen, ..^3);
Write(oneThroughTen, 3..^4);
Write(oneThroughTen, ^4..^2);

static void Write(int[] values, Range range) =>
    Console.WriteLine($"{range}:\t{string.Join(", ", values[range])}");
// Sample output:
//      0..^0:      1, 2, 3, 4, 5, 6, 7, 8, 9, 10
//      0..3:       1, 2, 3
//      2..^0:      3, 4, 5, 6, 7, 8, 9, 10
//      3..5:       4, 5
//      ^2..^0:     9, 10
//      0..^3:      1, 2, 3, 4, 5, 6, 7
//      3..^4:      4, 5, 6
//      ^4..^2:     7, 8
```