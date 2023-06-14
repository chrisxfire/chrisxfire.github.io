---
title: notes > .net > classes > fields
date: 2021-12-30T16:57:31-0700
draft: false
---
# Fields
Field – a variable of any type declared in a class or struct.
- If a field is static, every instance points to the same copy of the field in the type.
- If a field is readonly, its value can only be assigned during initialization or in a constructor.
- A static readonly field is like a const, except that the compiler can only access its value at run time.
- Usually private or protected with public *properties, methods, or indexers* that get or set their values.
- A private field that stores data exposed by a public property is a *backing field*.
- Fields are initialized immediately before the constructor for the object instance is called.

```cs
public class CalendarEntry 
{
    private DateTime _date; // A backing field.

    public DateTime Date 
    { // Property that exposes _date field safely.
        get { return _date; }
        set 
        {
            if (value.Year > 1900 && value.Year <= DateTime.Today.Year)
                _date = value;
            else
                throw new ArgumentOutOfRangeException();
        }
    }

    public void SetDate(string dateString) 
    { // A method that also exposes _date field safely.
        DateTime dt = Convert.ToDateTime(dateString);

        if (dt.Year > 1900 && dt.Year <= DateTime.Today.Year)
            _date = dt;
        else
            throw new ArgumentOutOfRangeException();
    }
}
```

There are 3 specialized categories of fields:
- `const` The data never changes. Constant fields are essentially static.
- `readonly` The data cannot change after the class is instantiated, but it can be calculated or loaded from an external source at the time of instantiation. This is often a better choice than `const`.
- `event` The data references a method that executes when something happens (ie: clicking on a button).
