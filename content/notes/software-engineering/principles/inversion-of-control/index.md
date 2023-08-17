---
title: inversion of control
date: 2022-01-01T00:00:00-06:00
draft: false
weight: 1
---

# Inversion of Control (Dependency Inversion)
If class `A` calls a method of class `B`, and class `B` calls a method of class `C`, then, at compile time, class `A` will *depend on* class `B`, and class `B` will depend on class `C`:  
<img alt="" src="dependency-inversion-1.png" width="40%" height="40%">

Instead, class `A` can call methods on an abstraction that `B` implements.  `B` depends on an interface controlled by `A` at compile time:
<img alt="" src="dependency-inversion-2.png" width="50%" height="50%">

This inverts the dependency.  
Dependency inversion is what enables dependency injection.