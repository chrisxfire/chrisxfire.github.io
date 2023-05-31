---
title: "notes > swe > principles > prefer composition over inheritance"
date: 2023-03-16T17:38:39-0600
draft: true
---
# Prefer Composition over Inheritance
## Inheritance is the specialization of a general concept
- Creates *Is-A* relationships.
- The derived class is *tightly coupled* to the base class.
- There is no additional performance cost of invoking the base class members.
- The Liskov Substitution Principle states that "*objects of a base class shall be replaceable with objects of its derived classes without breaking the application*."

public class House {
public string Color { get; set; }
public string GetAddress() => "Address";
}

public class GlassHouse : House {
public string WarningSign() => "No rocks please!";
}

## Composition is the association of objects of different classes
- Creates *Has-A* relationships.
- The class is *loosely coupled* to the component objects.
- Component objects must not be exposed.
- There is additional performance cost of invoking the component objects.

public class House {
private readonly Ceiling _ceiling;
private readonly Floor _floor;
public House() {
_ceiling = new Ceiling();
_floor = new Floor();
}

public string GetCeiling() => _ceiling.BuildCeiling();

public string GetFloor() => _floor.BuildFloor();
}

## Principle
Classes should achieve polymorphic behavior and code reuse by containing instances of other classes that implement the desired functionality (*composition*) rather than *inheritance* from a base class.

*Composition over inheritance* is practiced by:
- Creating interfaces that represent the behaviors that the system must exhibit;
- Creating classes that implement these interfaces and adding them to business domain classes.

We prefer composition over inheritance because:
- Inhertiance could lead to a deep hierarchy of classes (and a change at the bottom ripples down).
- Derived classes is exposed to all functionality of the base class – even when it doesn't need it.

Use composition over inheritance when:
- Your subclasses start to have subclasses.
- You need to do multiple inheritance.

## Another Example
[Composition Over Inheritance Design Pattern in C# – ScottLilly.com](https://scottlilly.com/c-design-patterns-composition-over-inheritance/)