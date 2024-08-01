---
title: index and range
date: 2022-01-09T19:17:18-0700
draft: false
weight: 1
---
# Index
Normally, the index is an integer passed to the indexer of an array:
```cs
int index = 3;
Person p = people[index]; // The fourth Person in the array.
```
The `Index` value type can identify position.

## <u>Creating</u>
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
# Range
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
