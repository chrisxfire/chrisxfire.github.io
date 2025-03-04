---
title: linked lists
date: 2021-11-15T14:18:34-0700
draft: false
weight: 1
---

# [Linked Lists](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.linkedlist-1?view=net-6.0)
Namespace  
`Systems.Collections.Generic`
Inheritance  
`Object` –> `LinkedList<T>`

A doubly-linked list. Each element is a *node* which has a reference to its previous and next items.
- Nodes are ordered one after another.
- Nodes are not stored contiguously.
- Nodes are linked using pointers.
- Nodes do not have indices.
The size of a linked list is dynamic.

Linked Lists provide better performance compared to Lists when frequently inserting and removing items from the middle of the list.

# construction
```cs
var ll = new LinkedList<type>();
```
# methods
## manipulating
```cs
.AddLast(elem) // Adds data to the end of the linked list.
```
## searching
```cs
.Contains(elem) // Boolean if elem is in the linked list.
```
## properties
`.CountReturns` the number of elements in the linked list.  
5 <–> 8 <–> 13 <–> Null
