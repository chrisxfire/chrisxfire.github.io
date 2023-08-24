---
title: concurrent
date: 2021-12-23T11:36:04-0700
draft: false
weight: 1
---
# [System.Collections.Concurrent](https://docs.microsoft.com/en-us/dotnet/api/system.collections.concurrent?view=net-6.0)
Efficient, thread-safe operations for access collection items from multiple threads.
Concurrent collection classes do not require user code to take any locks when accessing items.

- `BlockingCollection<T>` — provides blocking & bounding capabilities;
  - Producer threads block if not slots are available or if collection is full.
  - Consumer threads block if collection is empty.
  - Class can be used as backing store to provide blocking & bounding for any collection that implements `IEnumerable<T>`.
- `ConcurrentBag<T>` — Use for scalable add/get operations.
- `ConcurrentDictionary<Tkey, Tvalue>`
- `ConcurrentQueue<T>` — FIFO
- `ConcurrentStack<T>` — LIFO
