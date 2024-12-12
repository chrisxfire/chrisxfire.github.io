---
title: where clause
date: 2022-04-25T21:06:54-0600
draft: false
weight: 1
---

# Where clause
Use the `where` clause to *filter* out elements from the data based on one or more predicate expressions:

```cs
IEnumerable<City> queryCityPop =
    from city in cities
    where city.Population < 200_000 && city.Population > 100_000 // One predicate, two conditions.
    select city;
```
