---
title: inheritance
date: 2023-07-23T00:00:00-06:00
draft: false
weight: 1
---

# overview
EF Core supports three strategies of mapping .NET types:
- Table-per-Hierarchy (TPH) — the default strategy; maps .NET types to a single database table
  - Documentation: https://learn.microsoft.com/en-us/ef/core/modeling/inheritance#table-per-hierarchy-and-discriminator-configuration
- Table-per-Type (TPT) — maps each .NET type to a different database table
  - Documentation: https://learn.microsoft.com/en-us/ef/core/modeling/inheritance#table-per-type-configuration
- Table-per-Concrete-Type (TPC)
  > [!IMPORTANT]
  > Availability: EF Core 7
  - Like TPT, but in a way that addresses problems with that strategy.
  - Documentation: https://learn.microsoft.com/en-us/ef/core/what-is-new/ef-core-7.0/whatsnew#table-per-concrete-type-tpc-inheritance-mapping
By default, EF Core maps an inheritance hierarchy of .NET types to a single hierarchy.

# guidance
- Prefer TPH unless the below applies.
- Use TPC when code will mostly query for entities of a single leaf type.
- Use TPT only if constrained to do so by external factors.
