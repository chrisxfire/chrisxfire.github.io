---
title: join clause
date: 2022-04-27T18:45:49-0600
draft: false
weight: 1
---
# Join clause
Use `join` to associate and/or combine elements from one data source with elements from another based on an equality comparison between keys in each element.  
After you have joined two sequences, you must use a `select` or `group` statement to specify which element to store in the output sequence.

```cs
var categoryQuery =
    from cat in categories // `categories` is a string array.
    // join `prod` objects whose `Category` property matches one of the categories in the `categories` string array:
    join prod in products on cat equals prod.Category
    select new // anonymous type
    {
        Category = cat,
        Name = prod.Name
    };
```
