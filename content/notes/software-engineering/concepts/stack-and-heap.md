---
title: stack and heap
date: 2022-01-02T21:54:37-0700
draft: false
weight: 1
---

# Heap and Stack
The *stack* and *heap* can be anywhere in physical or virtual memory.  

The *heap* is memory set aside for dynamic allocation:
- Allocated when the application starts by the runtime.
- Managed by the Garbage Collector.
- Data stored on the heap is valid as long as it can be tracked back to a *reference type* variable on a stack.
  - When no more pointers point to the data, it becomes *garbage*.
- Heap memory is reclaimed when the application exits.

The *stack* is memory set aside as overhead space for a thread of execution:  
- It is faster than *heap* memory because:
  - It is managed directly by the CPU
  - It uses a LIFO mechanism (most recently reserved block is the first to be freed), which means it is more likely to have the data in its L1 or L2 cache.
- It is a consecutive block of memory that is allocated when a thread is first created.
- Every function call in a thread shares the same stack.
- The *stack pointer* points to the last location where memory was allocated.
- When a function is invoked, a new *stack frame* is created for that function's data.
- When a function exits, its return values are copied back to the calling function via the stack:
  - The stack pointer is then moved back to the beginning of the stack frame.
- When the thread exits, the stack is reclaimed (or reused by the next thread).
