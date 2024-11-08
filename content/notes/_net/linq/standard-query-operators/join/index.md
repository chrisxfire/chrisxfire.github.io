---
title: join
date: 2022-11-10T20:06:48-0700
draft: false
weight: 1
---
A jon operation is the association of objects in one data source with objects that share a common attribute in another data source.

Join operations target data sources whose relationships to each other cannot be followed directly.

# Join Type
In LINQ, `Join` implements an *inner join*.  
`GroupJoin` has no direct equivalent in relational database terms.  
It implements a superset of *inner joins* and *outer joins.*  

# Methods
| Method    | Description                                                                                           | Query expression                 |
|-----------|-------------------------------------------------------------------------------------------------------|----------------------------------|
| `Join`      | Join two sequences based on key-selector functions and extract pairs of values.                       | join … in … on … equals …        |
| `GroupJoin` | Join two sequences based on key-selector functions and group the resulting matches from each element. | join … in … on … equals … into … |

![](./Standard-Query-Operators_Join-image1.png)
