---
title: "notes > asp.net > reading > architecting modern web apps > develop asp.net core mvc apps > 6. domain driven design"
date: 2023-04-14T00:00:00-06:00
draft: false
---

Domain-Driven Design is an agile approach to building software that emphasizes a focus on the business domain.  The same terminology is used for the real-world concept being modeled, the software equivalent, and any structures to persist the concept (like database tables).

The domain model is made up of objects that interact with one another to represent the behavior of the system and includes:
- **Entities** — represent objects with a thread of identity; usually stored in persistence with a key
- **Aggregates** — groups of objects that should be persisted as a unit
- **Value objects** — concepts that can be compared on the basis of the sum of their property values (like DateRange consisting of a start and end date)
- **Domain events** — things happenging within the system that are of interest to other parts of the system

Use DDD for large applications with significant business complexity.


