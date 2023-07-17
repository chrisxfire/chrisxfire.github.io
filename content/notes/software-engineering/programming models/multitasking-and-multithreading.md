---
title: notes > software engineering > programming models > multitasking and multithreading
date: 2022-03-19T16:03:07-0600
draft: false
weight: 1
---
# Multitasking
In *cooperative multitasking*, the OS never initiates a context switch from one process to another. Processes voluntarily yield control periodically or when idle or when blocked.  

In *preemtive multitasking*, the OS initiates context switching through interruptions based on its scheduler.  

# Processors
Processes split themselves into multiple logical cores per physical core if they support multithreading.

## Multiprocessing
A system supports *multiprocessing* if it has multiple processors or multiple processor cores on a single integrated circuit.  
Multiprocessing allows multiple threads to execute in parallel; every processor or core executes a thread simultaneously. This is contrasted with concurrency in multithreading paradigms.  

# Processes
Processes are a unit of resources. They consist of one or more threads that share the process's resources (like memory, file handles, sockets, device handles, windows, etc).    
Creating, destroying, and switching processes is expensive.    

Processes are usually preemptively multitasked.  

## Kernel Level
A kernel level process contains one or more kernel threads.  

## User Level
A user level process contains one or more user threads.  

# Threads
A *thread* of execution is the smallest sequence of instructions that can be managed by a scheduler.  
- It is a component of a process.  
- Multiple threads in a process may be executed concurrently via multithreading.  
  - Threads of a process share their executable code and the value of their dynamically allocated variables.

Because they share the same address space, one thread can crash an entire process of threads.  

## Kernel Threads
At least one kernel thread exists within each process.  
Kernel threads are preemptively multitasked if the OS's scheduler is preemptive.  
Kernel threads are relatively cheap.  

## User Threads
User threads are threads that are implemented in userspace libraries.  
The kernel is unaware of user threads.  

If a user thread performs a system call that blocks, the other user threads in the process are unable to run until the system call returns.
- This is why I/O, a blocking operation, should be performed asynchronously.
- When an I/O op is initiated, a system call is made and does not return until the I/O op is completed.

## Fibers
Fibers are an even lighter unit of scheduling that are cooperatively scheduled on user threads.
A running fiber must explicitly yield to allow another fiber to run.  
Fibers can be scheduled to run in any thread on the same process.  

# Threading Models
## 1:1 (Kernel-level threading)
One user thread mapped to one kernel thread (schedulable entities in the kernel).

## N:1 (User-level threading)
Many user threads mapped to one kernel thread.  
The kernel has no knowledge of the user threads.  

Pros:
- Fast context switching, even on kernels that do not support threading.

Cons:
- Cannot leverage multi-processors (there is never more than one thread being scheduled at a time).

## M:N (hybrid threading)
M number of user threads mapped to N number of kernel threads.  
This is "virtual processors."  

Pros:
- Fast context switching (avoid system calls).

Cons:
- Requires changes to both kernel and user-space code.
- Higher probability of priority inversion.

# Multithreading
Multithreading is what allows multiple threads to exist in a single process. The threads operate concurrently. Concurrency is contrasted with paralellism in multiprocessing paradigms.  

## Simultaneous Multithreading
Simultaneous multithreading (SMT), also known as hyper-threading, is hardware-dependent. A CPU supporting SMT allows physical processor cores to be split into virtual processors (usually 1 physical core to 2 virtual processors). The virtual processors can each run instructions from a thread. With two virtual processors, two threads can run simultaneously.  

## Temporal Multithreading
Temporal multithreading, also known as super-threading, is multithreading implemented by time slicing. The maximum time slice for a thread is usually limited to 100-200ms. Only 1 thread per core can run at a time.  

## Race Conditions
Multithreading can lead to race conditions. If an operation takes more than one CPU instruction and there are 2 or more threads of execution, the two threads could update a data structure at the same time and find it changing unexpectedly.  

### Mutex
A mutual exclusion "locks" a data structure until the current thread is done operating on it.
- On single-processor systems, a thread running into a locked mutex must sleep, which triggers a context switch.
- On multi-processor systems, a thread running into a locked mutex can poll the mutex in a spinlock.
  - A spinlock causes a thread trying to acquire it to wait and loop ("spin") while repeatedly checking whether the lock is available.

# Processes vs. Threads
|         | State Information | Address Space | Process Switching |
| ------- | ----------------- | ------------- | ----------------- |
| Process | Heavy             | Independent   | Fast              |
| Thread  | Light             | Shared        | Slow              |

# Scheduling
Scheduling occurs at the kernel or user level.
