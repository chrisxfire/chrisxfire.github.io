---
title: notes > dotnet > linq > clauses > into keyword
date: 2022-04-25T21:03:34-0600
draft: false
---
# Into keyword
The `into` keyword is used in a select or group clause to create a temporary identifier that stores a query.  
Use this when you must perform additional query operations on a query after a grouping or select operation:

```cs
// percentileQuery is an IEnumerable<IGrouping<int, Country>>
var percentileQuery =
    from country in countries
    let percentile = (int)country.Population / 10_000_000 // Group according to population in ranges of 10M.
    group country by percentile into countryGroup  // countryGroup is the temporary identifer.
    where countryGroup.Key >= 20 // Additional query operations.
    orderby countryGroup.Key
    select countryGroup;
```
