---
title: notes > asp.net > ef core > concurrency
date: 2023-05-22T00:00:00-06:00
draft: false
---

# Handling Concurrency Conflicts
## Handling Concurrent Deletes
When a concurrent delete of a database row is detected, EF Core throws a `DbUpdateConcurrencyException` exception.  Handle this exception to handle the conflict.

## Handling Concurrent Updates
A concurrent update of a database row can be detected.  This requires a `Timestamp` property with attribute:
```cs
[Timestamp]
public byte[]? Timestamp { get; set; }
```

Then, add a migration and update the database:
```powershell
PM> Add-Migration AddTimestamp
PM> update-database
```
