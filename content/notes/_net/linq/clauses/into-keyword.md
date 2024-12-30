---
title: into keyword
date: 2022-04-25T21:03:34-0600
draft: false
weight: 1
tags:
 - kb/dotnet/linq/clauses
---

# into keyword
The `into` keyword is used in a `select` or `group` clause to create a temporary identifier that stores a query.  
Use this when you must perform additional query operations on a query after a grouping or select operation:

```cs
// percentileQuery is an IEnumerable<IGrouping<int, Country>>
var percentileQuery =
    from country in countries
    let percentile = (int)country.Population / 10_000_000 // Group according to population in ranges of 10M.
    group country by percentile into countryGroup  // countryGroup is the temporary identifier.
    where countryGroup.Key >= 20 // Additional query operations.
    orderby countryGroup.Key
    select countryGroup;

// grouping is an IGrouping<int, Country>
foreach (var grouping in percentileQuery)
{
    Console.WriteLine(grouping.Key);
    foreach (var country in grouping)
    {
        Console.WriteLine(country.Name + ":" + country.Population);
    }
}
```

