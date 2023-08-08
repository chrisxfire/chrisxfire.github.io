---
title: overview
date: 2023-06-14T00:00:00-06:00
draft: false
weight: -1
---

# Overview
`DbContext` instances track changes made to their entities.  The tracked entities report the changes to the database when `SaveChanges` is called.  

Entity instances become tracked when they are: (1) returned from a query; (2) explicitly attached to a `DbContext` via `Add`, `Attach`, or `Update`; (3) detected as new entities connected to existing tracked entities.  

Entity instances are no longer tracked when: (1) the `DbContext` is disposed; (2) the change tracker is cleared; (3) the entities are explicitly detached.

Change tracking occurs at the *property* level.  If only a single property value is modified, then the database update will change only that value.

# Entity States
Every entity is associated with an `EntityState`.  The states:
- `Detached` — entity is not being tracked by DbContext
- `Added` — entity are new and not yet in the database
- `Unchanged` — entity not changed since queried from database
- `Modified` — entity changed since queried from database
- `Deleted` — entity exists in database but marked to be deleted when `SaveChanges` is called

Entity states rarely need to be manipulated manually.  Unless explicitly necessary, use the same `DbContext` instance for both querying entities and updating them via `SaveChanges`.

# Sequencing
EF Core will process database CRUD operations in this order:
1. INSERT
2. UPDATE
3. DELETE
