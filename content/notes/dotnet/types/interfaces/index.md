---
title: "notes > dotnet > types > interfaces"
date: 2021-11-05T21:26:07-0600
draft: true
---
# Interfaces
[Interfaces - define behavior for multiple types | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/fundamentals/types/interfaces)
[Safely update interfaces using default interface methods in C# | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/whats-new/tutorials/default-interface-methods-versions)
Interfaces require classes or structs to implement certain members. They define a *contract*. They define "*can-do*" relationships.
Interfaces can be declared in namespace or class scope.
Interfaces cannot contain *instance state*.

<table>
<colgroup>
<col style="width: 18%" />
<col style="width: 46%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th></th>
<th>May contain</th>
<th>Cannot</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>instance</td>
<td>methods, properties, events, indexers</td>
<td>fields, constructors, finalizers</td>
</tr>
<tr class="even">
<td>static</td>
<td>methods, fields, properties, events, indexers</td>
<td></td>
</tr>
<tr class="odd">
<td><p>static abstract</p>
<p>static virtual</p></td>
<td>methods, properties, events, indexers</td>
<td>fields</td>
</tr>
</tbody>
</table>

# Creating
interface IScored {
float Score { get; set; }
float MaximumScore { get; set; }
}

# Implementing 
Classes and structs implement interfaces.
- The implementing type <u>must</u> implement all members of the interface that do not have a default implementation.
- The implemented members must be public and non-static.

## Example 1
public class Person : object, IComparable<Person> { // Inherit from another class and an interface. Can also inherit
// … more implementation … // multiple interfaces.

public int CompareTo(Person? other) {
if (Name is null) { return 0; }
return Name.CompareTo(other?.Name); // Call the CompareTo method of the Name field. The Name field is a
} // string, so this uses string's implementation of CompareTo.
}

## Example 2
public class Car : IEquatable<Car> { // Class Car implements interface IEquatable<T>
public string Make { get; set; }
public string Model { get; set; }
public string Year { get; set; }

// Implementation of the IEquatable<T> interface by implementing it's only method:
public bool Equals(Car car) {
return (this.Make, this.Model, this.Year) == (car.Make, car.Model, car.Year);
}
}

# Interface Members
## Properties
In interfaces, declaring the get/set accessors without a body <u>does not</u> declare an auto-implemented property:
public Interface INamed {
public string Name { get; set; } // This property does not have a default implementation and must be implemented by a derived type.
}

Although interface properties may have default implementations, this is rare because interfaces cannot define instance data fields.

## Static Virtual/Abstract Members
Interfaces may define `static virtual` or `static abstract` members to declare that an implementing type must provide the declared members.
- Those interfaces can then be used as constraints to create generic types that use operators or other static methods.

`static virtual` methods are almost exclusively declared in generic interfaces.

Interface fields cannot be `static virtual`/`abstract`.

# Inheritance
- A type that inherits an interface <u>must</u> implement all of its members that do not have a default implementation.
- Types can inherit multiple interfaces (but only one base class).
- Interfaces may inherit from base interfaces.
- Interfaces are the only type a struct can inherit.

# Default Implementations
For interfance methods that define default implementations, any class inherting that interface also inherits that implementation.
- The class instance must be cast to the interface type to access the default implementation of the interface method.

## Versioning
C# allows an interface to add new members after release so long as they have a default implementation.
Default implementations are in effect whenever another implementation is not provided:

public interface IPlayable {
void Play();
void Pause();

void Stop() { // This member was added after release, so it requires a default implementation.
…
}
}

# Passing Interfaces like Types
Given this utility class:
public class ScoreUtility { // Of two assignments, return the one that has the higher score:
public static IScored BestOfTwo(IScored Assignment1, IScored Assignment2) {
// Assignment1 and Assignment2 both have the members of the IScored interface:
var score1 = Assignment1.Score / Assignment1.MaximumScore;
var score2 = Assignment2.Score / Assignment2.MaximumScore;

if (score1 >= score2)
return Assignment1;

else
return Assignment2;
}
}

## Don't Pass IEnumerable<T>
When a method that takes IEnumerable<T> as an input parameter performs iteration, it has to allocate an object on the heap. This is because the IEnumerator<T> GetEnumerator() method returns a reference type.

Instead, pass a concrete type, list List<T>.

# Common Interfaces
<table>
<colgroup>
<col style="width: 20%" />
<col style="width: 27%" />
<col style="width: 52%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Interface</strong></th>
<th><strong>Method(s)</strong></th>
<th><strong>Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>IComparable</td>
<td>CompareTo(other)</td>
<td>A comparison method that a <em>type</em> implements to sort its instances.</td>
</tr>
<tr class="even">
<td>IComparer</td>
<td>Compare(first, second)</td>
<td>A comparison method that a secondary type implements to sort instances of a primary type.</td>
</tr>
<tr class="odd">
<td>IDisposable</td>
<td>Dispose</td>
<td>A method to release unmanaged resources more efficiently than waiting for a finalizer.</td>
</tr>
<tr class="even">
<td>IFormattable</td>
<td>ToString(format, culture)</td>
<td>A culture-aware method to format the value of an object into a string.</td>
</tr>
<tr class="odd">
<td>IFormatter</td>
<td><p>Serailize(stream, object)</p>
<p>Deserialize(stream)</p></td>
<td>Methods to convert an object to and from a stream of bytes.</td>
</tr>
<tr class="even">
<td>IFormatProvider</td>
<td>GetFormat(type)</td>
<td>A method to format inputs based on language and region.</td>
</tr>
<tr class="odd">
<td>IEnumerable</td>
<td>GeEnumerator</td>
<td></td>
</tr>
<tr class="even">
<td>ICollection</td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

## Using IComparable vs. IComparer
If you're working with a *type* for which you do not have the source code, you cannot implement `IComparable`.
Instead, create a separate type that implements `IComparer`:

public class PersonComparer : IComparer<Person> {
public int Compare(Person? x, Person? y) {
if (x is null || y is null) { return 0; }
int result = x.Name.Length.CompareTo(y.Name.Length); // Compare the Name lengths…

if (result == 0) { // If they are equal…
return x.Name.Compareto(y.Name); // …then compare by the Names…
}
else { 
return result;  // …otherwise, compare by the Lengths.
}
}
}
