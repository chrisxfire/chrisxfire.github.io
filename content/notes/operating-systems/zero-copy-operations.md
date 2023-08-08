---
title: zero copy operations
date: 2023-06-24T00:00:00-06:00
draft: false
weight: 1
---

# Zero-copy Operations
- Zero-copy operations are data copy operations that do not need to copy between kernel and userspace
- This reduces kernel <--> userspace context switches
- These operations are also used in device drivers, file systems, and network stacks
