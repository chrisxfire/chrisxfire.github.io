---
title: threads
date: 2023-08-06T00:00:00-06:00
draft: false
weight: 1
---

# Overview
`Object` –> `CriticalFinalizerObject` –> `Thread`  
- Creates and controls a thread, sets its priority, and gets its status.
- Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.threading.thread?view=net-6.0

# Synchronizing Access to Shared Resources
## Monitor
Synchronize access to objects.
- The `Monitor` class allows you to synchronize access to a region of code by taking and releasing a lock on a particular object by calling the `Monitor.Enter`, `Monitor.TryEnter`, and `Monitor.Exit` methods.
- You can also use the `Monitor` class to ensure that no other thread is allowed to access a section of application code being executed by the lock owner, unless the other thread is executing the code using a different locked object.
- Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.threading.monitor?view=net-6.0

## Semaphore
Use the `Semaphore` class to control access to a pool of resources.
- Threads enter the semaphore by calling the `WaitOne` method, which is inherited from the `WaitHandle` class, and release the semaphore by calling the `Release` method.
- Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.threading.semaphore?view=net-6.0

## Mutex
A synchronization primitive that can also be used for inter-process synchronization.
- `Mutex` is a synchronization primitive that grants exclusive access to the shared resource to only one thread.
- If a thread acquires a mutex, the second thread that wants to acquire that mutex is suspended until the first thread releases the mutex.
- Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.threading.mutex?view=net-6.0

## Interlocked
Provides atomic operations for variables that are shared by multiple threads.
- The methods of this class help protect against errors that can occur when the scheduler switches contexts while a thread is updating a variable that can be accessed by other threads, or when two threads are executing concurrently on separate processors.
- The members of this class do not throw exceptions.
- Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.threading.interlocked?view=net-6.0
