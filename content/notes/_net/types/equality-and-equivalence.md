---
title: equality and equivalence
date: 2022-02-16T16:37:48-0700
draft: false
weight: 1
---
Equality Comparisons
Two types of Equality:
- Equivalence (value equality)
- Identity (reference equality)

# Reference Equality (Identity)
Objects have the same identity (or reference equality) if they refer to the same location in memory.

## Comparisons
Use `ReferenceEquals`:
```cs
areEqual = Object.ReferenceEquals(var1, var2);
```

## Notes
Never test for reference equality on strings. Although string is a reference type, its equality operators have been overridden to make them behave like value types.

# Value Equality (Equivalence)
Objects have the same equivalence (or value equality) based on abstract definitions. In some cases, the definition is that:
1.  They must be of the same type
2.  All of their fields and properties must have the same value

## Five Guarantees of Equivalence
Assuming that `x`, `y`, and `z` are not null:
1.  `x.Equals(x) == true` (reflexive property)
2.  `x.Equals(y) == y.Equals(x)` (symmetric property)
3.  `if (x.Equals(y) && y.Equals(z) == true`, then `x.Equals(z) == true` (transitive property)
4.  `x.Equals(y)` is omnipotent
5.  Any non-null value != null

## Notes
If you use `ReferenceEquals` to test two variables for value equality, the result will always be false (because each variable is boxed into a separate object instance).

# Implementing Value Equality in Classes and Structs
1.  Implement `System.IEquatable<T>` interface by providing a type-specific `Equals` method
    1.  Do not throw exceptions from this method.
    2.  This method must examine only fields that are declared in the class.
    3.  This method must call base.Equals to examine fields in the base class.
        1.  If the type inherits directly from Object, do not call base.Equals (Object's implementation of Equals performs a reference equality check).
2.  Override the virtual `Object.Equals(Object)` method
3.  (optional) Overload the == and != operators
4.  Override Object.GetHashCode such that two objects of this type that have value equality produce the same hash
5.  (optional) Implement IComparable<T> interface and overload <= and >= operators

## Example Implementation
```cs
class Person : IEquatable<Person>
{
    public int Age { get; set; }
    public string FirstName { get; set; }
    public string LastName { get; set; }

    public Person(string firstName, string lastName, int age)
    {
        this.FirstName = firstName;
        this.LastName = lastName;
        this.Age = age;
    }

    // #2
    public override bool Equals(object obj) => this.Equals(obj as Person);

    // #1
    public bool Equals(Person p)
    {
        if (p is null)
            return false;

        // Optimization of a common success case:
        if (Object.ReferenceEquals(this, p))
            return true;

        if (this.GetType() != p.GetType())
            return false;

        // #1(b)
        return (Age == p.Age) && (FirstName == p.FirstName) && (LastName == p.LastName);
    }

    // #4
    public override int GetHashCode() => (Age, FirstName, LastName).GetHashCode();

    // #3
    public static bool operator ==(Person lhs, Person rhs)
    {
        if (lhs is null)
        {
            if (rhs is null)
                return true;

            // Only left side is null:
            return false;
        }
    }

    return lhs.Equals(rhs);

    public static bool operator !=(Person lhs, Person rhs) => !(lhs == rhs);
}
