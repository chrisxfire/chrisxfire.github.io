---
title: notes > swe > algorithms
date: 2022-02-17T19:00:29-0700
draft: true
---
# Algorithms
Algorithm – Series of instructions that perform a task.

## Big-O Notation 
Used to describe time complexities, space complexities
- `O(1)` O of 1 time aka constant time
- `O(n)` Linear time
- `O(log(n))` Logarithmic time
- `O(n^2)` Exponential timeLeast efficient
- `O(n!)` Factorial time

## Linked Lists
Elements are ordered one after another. They are not stored in contiguous locations. They are linked using pointers. 

Linked Lists do not have indices. Each element is a node, which contains data and a reference to the next node. Size of a linked list is dynamic.

`ele0 ele1 ele2 ele3`  
`5 –> 8 –> 10 –> 13 –> null`  
head is `5`  
tail is `null`  

setting 10 to null results in:  
`5 –> 8 –> null`

## Queues
A queue contains elements in the order they were added.  
Queues are FIFO: Elements are inserted at the end (enqueue) and removed from the beginning (dequeue).  
Queues do not have indicies.

## Trees
A collection of nodes where each node can be linked to more nodes. Nodes are collected by links. Useful for nonlinear data.