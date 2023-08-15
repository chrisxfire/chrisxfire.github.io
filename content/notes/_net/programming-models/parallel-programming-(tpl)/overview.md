---
title: overview
date: 2023-02-16T14:28:40-0700
draft: false
weight: -1
---
# Overview
*Data parallelism* — scenarios in which the same operation is performed concurrently on elements in a collection.

# Task Parallel Library
Enables data parallelism through `System.Threading.Tasks.Parallel`.
Provides method-based parallel implementations of `for` and `foreach` loops.
Does not require engineer to create threads or queue work items.

## How it Works
When a parallel loop runs, TPL partitions the collection so that the loop can operate on multiple parts concurrently. TPL partitions the collection based on system resources and workload. The scheduler redistributes work among multiple threads and processors as needed.

# Design & Performance
- When parallelizing, one goal is to utilize the processors as much as possible without over parallelizing to the point where the overhead for parallel processing negates the performance benefit of the parallelism.
  - Often, this means parallelizing an outer or inner loop but not the other.
- In parallel loops, synchronous calls (like `Console.WriteLine`) will significantly degrade performance.

# Data Structures
## [Systems.Collections.Concurrent](https://learn.microsoft.com/en-us/_net/standard/collections/thread-safe/)
Efficient, thread-safe operations for access collection items from multiple threads.
Concurrent collection classes do not require user code to take any locks when accessing items.

Types:
- `BlockingCollection<T>` — provides blocking & bounding capabilities;
  - Producer threads block if not slots are available or if collection is full.
  - Consumer threads block if collection is empty.
  - Class can be used as backing store to provide blocking & bounding for any collection that implements `IEnumerable<T>`.
- `ConcurrentBag<T>` — Use for scalable add/get operations.
- `ConcurrentDictionary<Tkey, Tvalue>`
- `ConcurrentQueue<T>` — FIFO
- `ConcurrentStack<T>` — LIFO

## Systems.Threading
Primitives for fine-grained concurrency and faster performance than legacy code.

Types:
- `Barrier`—enables multiple threads to work on an algorithm in parallel; provides a point at which each task can signal its arrival and then block until some or all tasks have arrived.
- `CountdownEvent` — simplifies fork & join scenarios.
- `ManualResetEventSlim` — similar to `ManualResetEvent` but lighter weight, only for intra-process communication.
- `SemaphoreSlim` — limits the number of threads that can concurrently access a resource or pool of resources.
- `SpinLock` — a mutex lock primitive that causes the thread trying to acquire the lock to loop (*spin*) before yielding. Use when wait fo the lock is expected to be short.
- `SpinWait` — like `SpinLock` but spins for a specified amount of time before putting thread into wait state.

## [Lazy Initialization](https://learn.microsoft.com/en-us/_net/framework/performance/lazy-initialization)
With lazy initialization, memory for an object is not allocated until it is needed. Spreads object allocations evenly across the lifetime of an app.
Enable lazy initialization for any custom type by wrapping `System.Lazy<T>`.

`System.Threading.ThreadLocal<T>` — provides a lazily-initialized value on a per-thread basis with each thread lazily-invoking the initialization function.
`System.Threading.LazyInitializer` — static methods that avoid the need to allocate a dedicated, lazy-initialization instance; they use references to ensure targets are initialized as they are accessed.
