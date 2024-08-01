---
title: generic delegates
date: 2022-04-28T20:40:46-0600
draft: false
weight: 1
---

# Overview
Below are generic delegates useful for manipulating arrays and lists.

# Action\<T\>
Represents a method that performs some action on an element of the specified type.

Usage:
1. Create a method that performs the desired action on an element
2. Create an instance of the `Action<T>` delegate
3. Pass the array and the delegate to the `Array.ForEach` static generic method

Note: `List<T>` also has a `ForEach` method that uses an `Action<T>` delegate, but this method is not generic.

# Predicate\<T\>
Represents a method that determines whether a particular element meets defined criteria.

Usage:
1. Create a method that performs the desired test
2. Create an instance of the `Predicate<T>` delegate
3. Call `Array`'s methods that use this delegate: `Exists`, `Find`, `FindAll`, `FindIndex`, `FindLast`, `FindLastIndex`, `TrueForAll`.

Note: `List<T>` also has instance methods that accept `Predicate<T>`.

# Comparison\<T\>
Use to provide a sort order for an array or list that does not have a native sort order.

Usage:
1. Create a method that performs the comparison
2. Create an instance of the `Comparison<T>` delegate
3. Call the `Array.Sort<T>` or `List<T>.Sort()` methods

# Converter\<T\>
Use to define a conversion between two types including between arrays of different types and between lists of different types.

Usage:
1. Create a method that converts the elements of the existing list to a new type
2. Create an instance of the `Converter<T>` delegate
3. Call the `Array.ConvertAll` or `List<T>.ConvertAll` methods
