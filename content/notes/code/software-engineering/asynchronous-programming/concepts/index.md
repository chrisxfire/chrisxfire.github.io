---
title: notes > code > software engineering > asynchronous programming > concepts
date: "2023-05-28T00:00:00-06:00"
draft: false
---

# Blocking
A blocking activity causes the thread (entire application) to hang.  
Potentially blocking activities:  web access, database access, working with files, working with images, WCF.

# Multitasking (from *Modern Cross-Platform Development*)
## Processes & Threads
- Process – has resources like memory and threads allocated to it.
- Threads – execute code, statement by statement.
	- By default, each process has only one thread.

## Preemptive Multitasking
Simulates parallel execution of tasks.
- Divides processor time among threads into time slices.
- The current thread is suspended when switched to another.
	- The context of the current thread is saved and the context of the next thread in thread queue is loaded.
	- This takes time and resources to accomplish.
