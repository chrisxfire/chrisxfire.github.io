---
title: notes > code > software engineering > principles > overview
date: 2023-03-16T17:24:53-0600
draft: false
---
# DRY – Don't repeat yourself

# Inversion of Control
A mechanism that allows high-level components to depend on abstraction rather than the concrete implementation of low-level components.

# Object-Oriented Programming
## Abstraction
- Allows creating classes that do not have full implementations in order for those classes to be inherited (and the implementation completed) by others.
- One class can provide an abstraction for another (or many).
- Base classes are often abstract. `Stream` is abstract; `FileStream` and `MemoryStream` are concrete.

## Composition
- Allows objects to be composed of other objects.
- A *Car* object can be composed of four *Wheel* objects, four *Seat* objects, and one *Engine* object.

## Encapsulation 
- Allows hiding the internal state and functionality of an object and only allowing access through a public set of functions.

## Inheritance
- Allows a derived class to inherit behavior from a base class.

## Polymorphism 
- A single interface for different types.
- Also: allows a derived class to override an inherited action.

# Principle of Least Astonishment
A component of a system should behave in a way that most users will expect it to behave.
If a feature has a high astonishment factor, it may be necessary to redesign the feature.
People are a part of the system. The design should match the user's experience, expectations, and mental models.

# Robustness Principle
Be conservative in what you send; be liberal in what you accept.
(Postel's law—Jon Postel when defining TCP)

Other versions:
Be contravariant in the input type and covariant in the output type.

# SOLID
- Single responsibility – each class has one responsibility.
- Open/Closed – code is open for extension and closed for changes.
- Liskov substitution – objects are replaceable with their subtypes.
- Interface segregation – each interface has one purpose.
- Dependency Inversion
  - High-level modules should not depend on low-level modules. Both should depend on abstractions.
  - Abstractions should not depend on details. Details should depend on abstractions.

# Ya Ain't Gonna Need It
Don't add layers of architecture that only may be needed in the future.

# Agile vs. Waterfall
Don't consider Waterfall dead.
Use Agile when innovating or discvoering a problem space.
Consider Waterfall when the problem space and scope of work is well-defined.
# 
# API Design Principles
## Single Owner Principle
- Only 1 service can write to a given component or piece of data.
- All other services must call that owner via the API.

# Team Dynamics Principles
## Borderless Engineering
The practice of engineers floating from team to team for short periods to assist with work.
