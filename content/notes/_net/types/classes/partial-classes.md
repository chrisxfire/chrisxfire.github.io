---
title: partial classes
date: 2022-03-06T18:16:55-0700
draft: false
weight: 1
---

# partial classes
The partial keyword indicates that other parts of the class, struct, or interface can be defined in the namespace.

# rules
1.  All the parts must use the partial keyword.
2.  If any part is declared `abstract`, then the whole type is considered `abstract`.
3.  If any part is declared `sealed`, then the whole type is considered `sealed`.
4.  If any part declares a base type, then the whole type inherits that class.
