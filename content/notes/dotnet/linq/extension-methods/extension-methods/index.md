---
title: "notes > dotnet > linq > extension methods > extension methods"
date: 2022-05-02T07:55:01-0600
draft: true
---
# [LINQ Extension Methods](https://docs.microsoft.com/en-us/dotnet/api/system.linq.enumerable?view=net-6.0)
LINQ extension methods are static methods of Enumerable type in System.LINQ and appended to any sequence.
Sequences are types which implement IEnumerable<T> like arrays, generic collections, etc.

# Method Syntax
Some queries must be expressed as a method call. Most commonly, the queries return a singleton numeric value, such as Sum, Max, Min, Average, etc:
List<int> numbers1 = new() { 5, 4, 1, 3, 9, 8, 6 };
List<int> numbers2 = new() { 15, 14, 11, 13, 19, 18, 16 };

double average = numbers1.Average(); // Query as a method call. This query executes immediately because it returns a singleton.

IEnumerable<int> concatQuery = numbers1.Concat(numbers2); // Query as a method call. This query will not execute until iterated over.

// If a method has Action or Func parameters, these are in the form of a lambda expression:
IEnumerable<int> largeNumbersQuery = numbers2.Where(c => c > 15);

# Extension Methods
<u>Seekers</u>
All, AnyReturns `true` if all or any of the items match the filter (or if the sequence contains the item).
ContainsReturns `true` if the sequence contains the item.

<u>Selectors</u>
FirstGet the first item in a sequence or throw an exception. Also: Last.
FirstOrDefaultGet the first item in a sequence or return the default value of the type. Also: LastOrDefault.
SingleGet the item that matches a specific filter, or throw an exception is there is not exactly one match.
SingleOrDefaultGet the item that matches a specific filter, or return the default value for the type.
ElementAtGet an item at a specified index position, or throw an exception.
- Note: when working with Span<T> sequences, pass an Index instead of an int.
ElementAtOrDefaultGet an item at a specified index position, or return the default value for the type.
SelectProject items into a different shape (a different type) and flatten a nested hierarchy of items.
SelectMany

<u>Sorters</u>
OrderBySort items by a specified field or property. Also: OrderByDescending.
ThenByAfter items are ordered, sort by an additional field or property. Also: ThenByDescending.
GroupByGroup and/or join two sequences. Also: GroupJoin, Join.

<u>Filters</u>
DistinctRemove duplicate items.
DistinctBy, ExceptBy, IntersectBy, UnionBy, MinBy, MaxBy.
- Perform comparisons on a subset of the item. For example, instead of removing duplicates by comparing an entire `Person` object, do so by comparing just their `LastName` and `DateOfBirth`.
OfTypeRemove items that do not match a specified type.

<u>Combiners</u>
Append, Concat, Prepend.
ZipMatch up items in two or three sequences based on position of those items in each sequence.
- If there are an unequal number of items in the sequences, some items will not have a matching partner.

<u>Aggregators</u>
Aggregate, Average, Count, LongCount, Max, Min, Sum.
- Note: Count checks if a `Count` property is implemented and returns its value. If not, it enumerates the entire sequence to count its values.
TryGetNonEnumeratedCountReturns count via the `Count` property; returns `false` if missing and sets out parameter to 0.

<u>Set Operations</u>
Except, Intersect, Union.

<u>Converters and Cast</u>
ToArray, ToList, ToDictionary, ToHashSet, ToLookup.
CastCast items of a specified type. This is useful to convert non-generic objects to a generic type.
ChunkSplit a sequence into sized batches.

# Non-Extension Methods
Empty<T>Returns an empty sequence of type `T`.
Range(start: *n*, count: *m*)Returns a sequence of *m* integers starting from *n* value.
Repeat(element: n, count: m)Returns a sequence of element *n* repeated *m* times.