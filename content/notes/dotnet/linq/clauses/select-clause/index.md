---
title: "notes > dotnet > linq > clauses > select clause"
date: 2022-04-25T20:59:19-0600
draft: false
---
# Select clause
A `select` clause produces all other types of sequences. A simple `select` clause just produces a sequence of the same type of objects as the objects in the data source:

```cs
IEnumerable<Country> sortedQuery =
    from country in countries
    orderby country.Area // Sort the elements in some new order.
    select country; // Produce a sequence of the reordered objects.
```

But it can also transform (*project*) data into sequences of new types:
```cs
var queryNameAndPop =
    from country in countries
    select new// Projects a sequence of anonymous types which contain
    { // only a subset of the fields in the original element.
        Name = country.Name,
        Pop = country.Population
    };

foreach (var item in queryNameAndPop) 
{
    // item.Name, item.Pop
}
```

Another example:
```cs
double[] radii = { 1, 2, 3 };

IEnumerable<string> output =
    from rad in radii
    select $"Area for circle with radius {rad} = {rad * rad * Math.PI:F2}";

// Or, in method syntax:
IEnumerable<string> output =
    radii.Select(rad => $"Area for circle with radius {rad} = {rad * rad * Math.PI:F2}";

foreach (string s in output)
    Console.WriteLine(s);
```