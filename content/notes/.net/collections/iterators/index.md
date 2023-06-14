---
title: notes > .net > collections > iterators
date: 2021-11-19T14:40:47-0700
draft: false
---
# Iterators
Iterators are objects that traverse a container. They yield return each element one at a time.
- Each time yield return is reached, the current location in code is remembered.
- The next time the iterator is called, execution restarts from that location.
Iterators return IEnumerable, IEnumberable<T> or IEnumerator, IEnumerator<T>.
In asynchronous operations, they return IAsyncEnumerable<T> or IAsyncEnumerator<T>.
Iterators can be a method or a *get* accessor.

# Creating Iterator Methods
```cs
public IEnumerable<int> EvenSequence(int firstnum, int lastnum) 
{
    for (var number = firstnum, number <= lastnum, number++) 
    {
        if (number % 2 == 0) 
        {
            yield return number; // When this statement is reached, an expression is returned, and the
        }                    // current location in code is remembered.
    }
}
```
or:
```cs
public static IEnumerable SomeNumbers() 
{
    yield return 7;
    yield return 1;
    yield return 9;
}
```
# Using Iterators
Iterators are called with a foreach statement:
```cs
foreach (int number in EvenSequence(5, 18)) 
{
    … // Each iteration of this body creates a call to the iterator function which proceeds to the
}     // next yield return statement.
```

Using Iterators with a Generic List
