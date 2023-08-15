---
title: class vs struct vs record
date: 2022-11-03T18:41:48-0600
draft: false
weight: 1
---
| Type / Feature | Memory | Semantics | Mutability | Equality            |
|----------------|--------|-----------|------------|---------------------|
| Class          | heap   | reference | mutable    | reference           |
| Record         | heap   | reference | immutable  | value               |
| Struct         | stack  | value     | mutable    | value (inefficient) |
