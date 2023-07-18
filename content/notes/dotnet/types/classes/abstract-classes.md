---
title: notes > .net > types > classes > abstract classes
date: 2022-02-17T20:25:50-0700
draft: false
weight: 1
---
# Abstract Classes
Abstract classes and members are incomplete and <u>must</u> be implemented in a derived class.
- They cannot be directly instantiated.
- They cannot be static.
- They *may* contain constructors.

# Abstract, Concrete, Virtual, and Static Members
Abstract classes may contain `abstract`, `concrete`, `virtual`, and `static` members:
- `abstract` members have no implementation.
  - They <u>must</u> be implemented in the derived class. Use the `override` keyword.
  - A field cannot be abstract.
  - They cannot be static.
- Concrete members have an implementation. They are inherited in the derived class like normal.
  - They *may* be re-implemented in the derived class with the `new` keyword.
  - They *may* be static.
- `virtual` members have an implementation. They are inherited in the derived class like normal.
  - They *may* be re-implemented in the derived class with the `override` keyword.
  - They cannot be static.
- `static` members have an implementation.
  - They may be re-implemented in the derived class with the `new` keyword.

| Member Modifier | Default Implementation | Re-implement | Keyword  | Static |
| --------------- | ---------------------- | ------------ | -------- | ------ |
| abstract        | No                     | Must         | override | No     |
| virtual         | Yes                    | May          | override | No     |
| (concrete)      | Yes                    | May          | new      | May    |
| static          | Yes                    | May          | new      | Yes    |

# Sealed
The `sealed` keyword prevents inheritance of a class, or of class members that were previously marked virtual.
Because a sealed class cannot be the base class of a derived class, it also cannot be abstract.
