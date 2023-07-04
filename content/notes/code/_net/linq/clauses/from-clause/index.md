---
title: notes > code > .net > linq > clauses > from clause
date: 2022-04-25T20:57:19-0600
draft: false
---
# Multiple From Clauses
Use additional from clauses when each element in the source is itself a collection or contains a collection.

```cs
IEnumerable<City> cityQuery =
    from country in countries // Here, countries is a collection of Country objects.
    from city in country.Cities // Here, Cities is a collection of City objects.
    where city.Population > 10000
    select city;
```
