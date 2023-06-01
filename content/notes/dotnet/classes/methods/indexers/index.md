---
title: "notes > dotnet > classes > methods > indexers"
date: 2021-11-06T11:26:41-0600
draft: false
---
# Indexers
Indexers (indexed properties) are Properties that can be indexed into some collection of values.  
They enable objects to be indexed like arrays.  
The compiler generates an Item property and the appropriate accessor methods.  

# Creating
The name of the member is this:  
```cs
public class Person
{
    // …

    public Person `this`[int index] 
    { // The indexer.
        // Avoid auto-implemented properties with indexers:
        get { return Children[index]; } // The get and set accessors make this indexer read-write.
        set 
        {
            Children[index] = value;
        }
    }
}
```

# Consuming (Using)
```cs
chris.Children.Add(new() { Name = "Noah" });
chris.Children.Add(new() { Name = "Eli" });
```

# Another Example
```cs
class SomeClass<T> 
{
    // An array to store data elements:
    private T[] arr = new T[100];

    // Define the indexer:
    public T this[int i] 
    {
        get { return arr[i]; }
        set { arr[i] = value; }
    }
}
```

# Example of Indexer That Searches by String Instead of Index
```cs
public int this[string day] = FindDayIndex(day);

private int FindDayIndex(string day) 
{
    for (int j = 0; j < days.Length; j++) 
    {
        if (days[j] == day) 
        {
            return j;
        }
    }
}
```

# Property vs. Indexer
| Property                                                                                                | Indexer                                                                                                                               |
|---------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
| Allows methods to be called like public data members.                                                   | Allows elements to be accessed via array notation.                                                                                    |
| Accessed by name.                                                                                       | Accessed by index.                                                                                                                    |
| Can be static or instance member.                                                                       | Must be instance member.                                                                                                              |
| `get` accessor has no parameters.                                               | `get` accessor has same formal parameter list as indexer.                                                     |
| `set` accessor contains the implicit `value` parameter. | `set` accessor has same formal parameter list as indexer, and also `value` parameter. |
|                                                                                                        |                                                                                                                                      |

Other use cases:
- Indexers are usually used in types whose primary purpose is to encapsulate an internal collection or array.
- Create Indexers when your type models an array or vector (`this [int idx]`).
- Model a dictionary or map (`this [string s]`).
- Model a multi-dimensional maps (`this [double x, double y]`).
