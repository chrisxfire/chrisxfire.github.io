---
title: notes > code > .net > types > reference types > objects > object and collection initializers
date: 2022-03-06T17:36:04-0700
draft: false
---
# Object Initializers
Objects can be initialized when declared. Using object initializers works even when the initialization doesn't match a constructor as long as a parameterless constructor exists.  

The compiler processes object initializers by first accessing the parameterless instance constructor and then processing the member initializations:

```cs
public class StudentName 
{
    public int ID { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }

    public StudentName() { } // This is the parameterless constructor that is accessed…

    public StudentName(string first, string last) 
    { // …not this one.
            FirstName = first;
            LastName = last;
    }

    // …more implementation…
}

StudentName student1 = new StudentName 
{ // This call access the parameterless constructor, not the 2-parameter
    FirstName = "John", // constructor.
    LastName = "Wick"
};
```

# Collection Initializers
A Dictionary of objects can be initialized with a collection initializer:

```cs
public class StudentName 
{
    public int ID { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }
}

var students = new Dictionary<int, StudentName>() 
{
    { 111, new StudentName { FirstName="Sachin", LastName="Karnik", ID=211 } },
    { 112, new StudentName { FirstName="Dina", LastName="Salimzianova", ID=317 } },
    { 113, new StudentName { FirstName="Andy", LastName="Ruth", ID=198 } }
}
```

## Index Initializers
Alternatively, a Dictionary of objects can be initialized with an index initializer:
```cs
var students2 = new Dictionary<int, StudentName>() 
{
    [111] = new StudentName { FirstName="Sachin", LastName="Karnik", ID=211 },
    [112] = new StudentName { FirstName="Dina", LastName="Salimzianova", ID=317 } ,
    [113] = new StudentName { FirstName="Andy", LastName="Ruth", ID=198 }
};
```
