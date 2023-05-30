---
title: "notes > dotnet > linq > clauses > orderby clause"
date: 2022-04-25T21:09:01-0600
draft: true
---
# Orderby clause
Use the orderby clause to *sort* results in either ascending or descending order. You can also specify a secondary sort:

IEnumerable<Country> querySortedCountries =
from country in countries
orderby country.Area, country.Population descending // Sort first by Area (ascending), then Population.
select country;