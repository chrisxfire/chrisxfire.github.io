---
title: threads
date: 2023-08-06T00:00:00-06:00
draft: false
weight: 1
---

# overview
`Object` –> `CriticalFinalizerObject` –> `Thread`  
- Creates and controls a thread, sets its priority, and gets its status.
- Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.threading.thread?view=net-6.0

# synchronizing access to shared resources
## `Monitor`
Synchronize access to objects.
- The `Monitor` class allows you to synchronize access to a region of code by taking and releasing a lock on a particular object by calling the `Monitor.Enter`, `Monitor.TryEnter`, and `Monitor.Exit` methods.
- You can also use the `Monitor` class to ensure that no other thread is allowed to access a section of application code being executed by the lock owner, unless the other thread is executing the code using a different locked object.
- Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.threading.monitor?view=net-6.0

## [`Lock`](https://learn.microsoft.com/en-us/dotnet/api/system.threading.lock?view=net-9.0)
The `Lock` class is used to define regions of code that require mutually exclusive access between threads of a process. These regions are called *critical sections*. `Lock`s are entered and exited, and the code between the enter and exit is the critical section. A thread that enters a lock is said to *hold* or *own* the lock until it exits the lock. Only one thread can hold a lock at any given time.

`Lock` objects have an `Enter` method:
- When the method returns, the current thread is the only thread that holds the lock.
- When the lock cannot be immediately entered, it waits.

`Lock` objects have a `TryEnter` method:
- The method returns boolean if the lock was entered by the current thread.
- When the method returns `true`, the current thread is the only thread that holds the lock.
- When the lock cannot be immediately entered, it returns `false`.

For both `Enter` and `TryEnter`: 
- These methods may throw a `LockRecursionException` if the lock reaches a limit of repeated entries by the current thread.
- If the current thread already holds the lock, the lock is entered again.

> [!WARNING]
> To fully exit the lock, the current thread must exit the lock as many times as it entered it.

`Lock` objects have an `EnterScope` method:
- The method returns a `Lock.Scope` that can be disposed of to exit the lock.
- When the lock cannot be immediately entered, it waits.
- This method is intended to be used with a `using` statement.

Examples:
```cs
public sealed class ExampleDataStructure
{
    private readonly Lock _lockObj = new();

    public void Modify()
    {
        lock (_lockObj)
        {
            // Critical section associated with _lockObj
        }

        using (_lockObj.EnterScope())
        {
            // Critical section associated with _lockObj
        }

        // The Enter() method enters the lock, waiting if necessary:
        _lockObj.Enter();
        try
        {
            // Critical section associated with _lockObj
        }
        finally { _lockObj.Exit(); }

        // The TryEnter() method enters the lock without waiting:
        if (_lockObj.TryEnter())
        {
            try
            {
                // Critical section associated with _lockObj
            }
            finally { _lockObj.Exit(); }
        }
    }
}
```

### `lock` statement
The `lock` statement works like a `using` statement with the `EnterScope` method of a `Lock`.

So, this...
```cs
lock (x)
{
    // ...
}
```

...is equivalent to this:
```cs
using (x.EnterScope())
{
    // ...
}
```

## `Semaphore`
Use the `Semaphore` class to control access to a pool of resources.
- Threads enter the semaphore by calling the `WaitOne` method, which is inherited from the `WaitHandle` class, and release the semaphore by calling the `Release` method.
- Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.threading.semaphore?view=net-6.0

## `Mutex`
A synchronization primitive that can also be used for inter-process synchronization.
- `Mutex` is a synchronization primitive that grants exclusive access to the shared resource to only one thread.
- If a thread acquires a mutex, the second thread that wants to acquire that mutex is suspended until the first thread releases the mutex.
- Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.threading.mutex?view=net-6.0

## `Interlocked`
Provides atomic operations for variables that are shared by multiple threads.
- The methods of this class help protect against errors that can occur when the scheduler switches contexts while a thread is updating a variable that can be accessed by other threads, or when two threads are executing concurrently on separate processors.
- The members of this class do not throw exceptions.
- Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.threading.interlocked?view=net-6.0
