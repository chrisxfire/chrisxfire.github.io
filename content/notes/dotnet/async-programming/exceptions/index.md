---
title: "notes > dotnet > async programming > exceptions"
date: 2022-02-16T16:30:13-0700
draft: false
---
# Exceptions
- When an async task throws an exception, that `Task` is *faulted*.
- The `Task` object holds the exception in the `Task.Exception` property.
- The exception is rethrown when the task is awaited.