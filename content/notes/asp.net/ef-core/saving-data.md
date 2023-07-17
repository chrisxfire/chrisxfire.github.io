---
title: notes > asp.net > ef core > saving data
date: 2023-05-24T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Two approaches:
  1. Change tracking and `SaveChanges`
  2. `ExecuteUpdate` and `ExecuteDelete` (bulk update)

# 1. Change tracking and `SaveChanges`
## Change Tracking
EF tracks loaded entities in its internal *change tracker*.  Whenever an entity is queried via LINQ, it is loaded.

## Pattern
The general pattern is to query some data from the database, modify it, and save the modified data back to the database:
```cs
using var context = new BloggingContext();
var blog = context.Blogs.Single(b => b.Url == "www.example.com"); // query
blog.Url = "www.example.com/blog"; // modify
context.SaveChanges(); // save
```

## Disadvantages
- `SaveChanges()` requires tracking (and, by extension, querying) all entities to be modified or deleted.  For example, deleting a large number of rows requires a corresponding `DELETE` statement for all of them.  RDBMS's support a single DELETE command, but the `SaveChanges()` approach does not support this.

# 2. `ExecuteUpdate` and `ExecuteDelete` (bulk update)  
<g>Availability:  EF Core 7.0</g>

## Pattern
```cs
context.Blogs.Where(b => b.Rating < 3).ExecuteDelete();
```

The above results in a single `DELETE` statement without loading any data from the database or involving the change tracker.

## Disadvantages
- Only updating and deleting operations are available.  Inserting must be done via `DbSet<T>.Add` and `SaveChanges()`.
- No automatic concurrency control when persisting changes.
- These methods execute immediately and cannot be batched.  `SaveChanges()` can batch multiple operations.
