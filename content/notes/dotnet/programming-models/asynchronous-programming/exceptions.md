---
title: notes > .net > programming models > asynchronous programming > exceptions
date: 2022-02-16T16:30:13-0700
draft: false
weight: 1
---
# Exceptions
- When an async task throws an exception, that `Task` is *faulted*.
- The `Task` object holds the exception in the `Task.Exception` property.
- The exception is re-thrown when the task is awaited.
