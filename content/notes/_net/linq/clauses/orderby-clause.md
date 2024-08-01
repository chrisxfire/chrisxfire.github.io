---
title: orderby clause
date: 2022-04-25T21:09:01-0600
draft: false
weight: 1
---
# Orderby clause
Use the `orderby` clause to *sort* results in either ascending or descending order. You can also specify a secondary sort:

```cs
IEnumerable<Country> querySortedCountries =
    from country in countries
    orderby country.Area, country.Population descending // Sort first by Area (ascending), then Population.
    select country;
```
