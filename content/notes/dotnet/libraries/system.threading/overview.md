---
title: notes > .net > libraries > system.threading > overview
date: 2023-06-15T00:00:00-06:00
draft: false
weight: -1
---
# Synchronizing Access to Shared Resources
## [Monitor](https://docs.microsoft.com/en-us/dotnet/api/system.threading.monitor?view=net-6.0)
Synchronize access to objects.
- The [Monitor](https://docs.microsoft.com/en-us/dotnet/api/system.threading.monitor?view=net-6.0) class allows you to synchronize access to a region of code by taking and releasing a lock on a particular object by calling the [Monitor.Enter](https://docs.microsoft.com/en-us/dotnet/api/system.threading.monitor.enter?view=net-6.0), [Monitor.TryEnter](https://docs.microsoft.com/en-us/dotnet/api/system.threading.monitor.tryenter?view=net-6.0), and [Monitor.Exit](https://docs.microsoft.com/en-us/dotnet/api/system.threading.monitor.exit?view=net-6.0) methods.
- You can also use the [Monitor](https://docs.microsoft.com/en-us/dotnet/api/system.threading.monitor?view=net-6.0) class to ensure that no other thread is allowed to access a section of application code being executed by the lock owner, unless the other thread is executing the code using a different locked object.

## [Semaphore](https://docs.microsoft.com/en-us/dotnet/api/system.threading.semaphore?view=net-6.0)
Use the [Semaphore](https://docs.microsoft.com/en-us/dotnet/api/system.threading.semaphore?view=net-6.0) class to control access to a pool of resources.
- Threads enter the semaphore by calling the [WaitOne](https://docs.microsoft.com/en-us/dotnet/api/system.threading.waithandle.waitone?view=net-6.0) method, which is inherited from the[WaitHandle](https://docs.microsoft.com/en-us/dotnet/api/system.threading.waithandle?view=net-6.0) class, and release the semaphore by calling the [Release](https://docs.microsoft.com/en-us/dotnet/api/system.threading.semaphore.release?view=net-6.0) method.

## [Mutex](https://docs.microsoft.com/en-us/dotnet/api/system.threading.mutex?view=net-6.0)
A synchronization primitive that can also be used for interprocess synchronization.
- [Mutex](https://docs.microsoft.com/en-us/dotnet/api/system.threading.mutex?view=net-6.0) is a synchronization primitive that grants exclusive access to the shared resource to only one thread.
- If a thread acquires a mutex, the second thread that wants to acquire that mutex is suspended until the first thread releases the mutex.

## [Interlocked](https://docs.microsoft.com/en-us/dotnet/api/system.threading.interlocked?view=net-6.0)
Provides atomic operations for variables that are shared by multiple threads.
- The methods of this class help protect against errors that can occur when the scheduler switches contexts while a thread is updating a variable that can be accessed by other threads, or when two threads are executing concurrently on separate processors.
- The members of this class do not throw exceptions.
