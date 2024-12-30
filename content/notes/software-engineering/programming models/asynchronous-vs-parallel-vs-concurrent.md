---
title: asynchronous vs parallel vs concurrent
date: 2023-02-16T14:38:58-0700
draft: false
weight: 1
---

# overview
- *Asynchronous* — executing a task one one thread while awaiting completion of another task currently being executed on another thread.
- *Concurrency* — executing the same task on two threads. Non-deterministic (the order in which different pieces of the task are complete is not known).
- *Parallel* — executing the same task on two threads. Deterministic (the order in which different pieces of the task are complete is known).
