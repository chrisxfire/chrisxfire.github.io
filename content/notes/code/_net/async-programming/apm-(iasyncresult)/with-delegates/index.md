---
title: notes > code > .net > async programming > apm (iasyncresult) > with delegates
date: 2023-02-17T08:54:08-0700
draft: false
---
# Overview
Delegates enable calling any synchronous method in an asynchronous manner.

# How it Works
The CLR automatically defines `BeginInvoke` and `EndInvoke` methods for a delegate with the appropriate signature. This can then be used like the APM model.

## BeginInvoke
- Has same parameters as method to be executed asynchronously, plus:
  1.  an `AsyncCallback` delegate that references the method to be called when the async call completes
  2.  a user-defined object that passes information into the callback method
- Returns an `IAsyncResult`

## EndInvoke
- If called before async call is complete, blocks calling thread until it is.
- Returns the result of the async call.

# Process
1.  Call `BeginInvoke`
2.  Either:
    1.  Do some work and then call `EndInvoke`
    2.  Wait
        1.  Obtain a `WaitHandle` from `IAsyncResult.AsyncWaitHandle`
        2.  Use it `WaitOne` method to block until the `WaitHandle` is signaled
        3.  Call `EndInvoke`
    3.  Poll
        1.  Poll `IAsyncResult` to determine when the async call has completed
        2.  Call `EndInvoke`
    4.  Pass a delegate for a callback method to `BeginInvoke`
        1.  This method is executed when the async call completes.
        2.  Have the callback method call `EndInvoke`.

Example
```cs
public class SomeClass
{
    public string SomeLongRunningMethod(int callDuration, out int threadId)
    {
        Thread.Sleep(callDuration);
        threadId = Thread.CurrentThread.ManagedThreadId;
        return $"Call time {callDuration.ToString()}";
    }

    public delegate string SomeDelegate(int callDuration, out int threadId);
}

public class SomeOtherClass
{
    public static void Main()
    {
    int threadId;

    SomeClass c = new();

    // Create the delegate:
    SomeDelegate caller = new(c.SomeLongRunningMethod);

    // Initiate the async call:
    IAsyncResult result = caller.BeginInvoke(3000, out threadId, null, null);

    // End the async call:
    string returnValue = caller.EndInvoke(out threadId, result);
    }
}
```
