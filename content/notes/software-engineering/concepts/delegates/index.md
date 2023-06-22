---
title: notes > software engineering > concepts > delegates
date: 2023-02-22T11:10:19-0700
draft: false
---
# Delegates
- A type-safe function pointer.
- A reference to a method.
- Delegate objects are passed to code that can then call the referenced method.
- Used to implement *callbacks* and *event listeners*.
- They create the ability to notify several methods that an event has occurred.
- Can also be used to call multiple methods at once (that match their signature).
