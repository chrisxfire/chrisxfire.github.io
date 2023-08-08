---
title: aggregate
date: 2022-11-13T19:07:11-0700
draft: false
weight: 1
---
An aggregate operation computes a single value from a collection.

# Methods
## Aggregate
`Aggregate<T1>(this IEnumerable<T> source, Func<T, T, T> function)`
- Performs an operation on the first two elements in the collection.
- It takes that result and performs an operation on the next element…
- …and so on for all elements.

```cs
var nums = new[]{1,2,3,4};
var sum = nums.Aggregate( (a,b) => a + b);
Console.WriteLine(sum); // output: 10 (1+2+3+4)
```

`Aggregate<T1>(this IEnumerable<T1> source, T2 seed, Func<T2, T1, T2> function)`
- Same as a above, but uses a seed value to start:

```cs
var multipliers = new []{10,20,30,40};
var multiplied = multipliers.Aggregate(5, (a,b) => a * b);
Console.WriteLine(multiplied); //Output 1200000 ((((5*10)*20)*30)*40)
```

## Average
Calculates the average value of a collection.

## Count
`Count<T1>(this IEnumerable<T1> source)`  
Counts the elements of a collection.

`Count<T1>(this IEnumerable<T1> source, Func<T, Boolean> function)`  
Counts only those elements that satisfy a predicate function.

## LongCount
Like count, but returns `Int64` instead of `Int32`.

## Max(By)
Returns the maximum value in a collection.

## Min(By)
Returns the minimum value in a collection.

## Sum
Calculates the sum of the values in a collection.
