---
title: notes > asp.net > ef core > saving data > executeupdate and executedelete
date: 2023-07-23T00:00:00-06:00
draft: false
weight: 1
---

# Overview
<g>Availability: EF Core 7</g>  
By default, EF Core tracks changes to entities and sends updates to the database with `SaveChanges{Async}`.  Sometimes it may be useful to execute update and/or delete commands on the database without involving the change tracker. EF7 enables this with `ExecuteUpdate{Async}` and `ExecuteDelete{Async}` methods.

`ExecuteUpdate{Async}` and `ExecuteDelete{Async}` are applied to a LINQ query and will update or delete entities in the database.

These methods complement—not replace—the existing `SaveChanges{Async}` methods.

Documentation:
- https://learn.microsoft.com/en-us/ef/core/what-is-new/ef-core-7.0/whatsnew#executeupdate-and-executedelete-bulk-updates
- https://learn.microsoft.com/en-us/ef/core/saving/execute-insert-update-delete