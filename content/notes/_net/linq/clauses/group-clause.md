---
title: group clause
date: 2022-04-25T20:57:23-0600
draft: false
weight: 1
---

# Group clause
The group clause produces a sequence of groups organized by a specified key. The key is specified after the by keyword.
```cs
var queryCountryGroups =
    from country in countries
    group country by country.Name[0]; // Here, country.Name[0] is the key.
```
