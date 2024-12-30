---
title: static classes
date: 2022-02-17T20:46:19-0700
draft: false
weight: 1
---

# static classes
Static classes:
- Contain only static members.
- Cannot be instantiated.
- Are implicitly sealed (cannot be derived from).
- Cannot contain instance constructors (only static constructors).

It is more common to declare a non-static class with some static members than to declare an entire class static.

If a class contains static fields, provide a static constructor to initialize them.

# static members
A non-static class *may* contain static methods, fields, properties, or events.
Static methods and properties cannot access non-static fields and events in their type.

## uses for static fields
1.  Keeping count of the number of objects that have been instantiated.
2.  Store a value that must be shared among all instances.
