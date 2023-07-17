---
title: notes > .net > programming models > asynchronous programming > asynchronous programming model (APM) (iasyncresult) > overview
date: 2023-02-14T17:14:31-0700
draft: false
weight: -1
---
# Pattern
Uses two methods: `BeginOperationName` and `EndOperationName`

`BeginOperationName`
- Contains the same parameters as the synchronous version of the method and two additional parameters:
  1.  An `AsyncCallback` delegate that references a method that is called when the async op completes
  2.  A user-defined object
- Returns an `IAsyncResult`

`IAsyncResult`
- Members:
  - `AsyncState`
  - `AsyncWaitHandle`
  - `CompletedSynchronously`
  - `IsCompleted`

`EndOperationName`
- Contains the same parameters as the synchronous counterpart and an `IAsyncResult` parameter
- The `IAsyncResult` passed in must be the same one that originated from the `BeginOperationName` method
  - Passing other `IAsyncResult` objects is undefined.
  - Calling `EndOperationName` multiple times with the same `IAsyncResult` object is undefined.

# Sequencing
1.  Call BeginOperationName
2.  If there is additional work to perform (blocking is not needed), either:
    1.  Poll for operation completion status by checking `IsCompleted` periodically, then call `EndOperationName` when op is complete
    2.  Use an AsyncCallback
3.  If blocking is needed (no additional work to be performed), either:
    1.  Call `EndOperationName` from the app's main thread. This blocks execution until the op is complete.
    2.  Use the `AsyncWaitHandle` to block until one or more ops completes.

# Performing additional work (no blocking needed)
## Polling for operation completion
`IAsyncResult result = BeginOperationName(…, null, null);`

`while (result.IsCompleted != true)`
`{`
    `// Do additional work`
`}`

`var returnValue = EndOperationName(result);`

## Use `AsyncCallback`

# Block until async op completes (no additional work to perform)
## Call `EndOperationName`

## Use `AsyncWaitHandle`
