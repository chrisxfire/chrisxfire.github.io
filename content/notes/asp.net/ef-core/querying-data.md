---
title: querying data
date: 2023-05-23T00:00:00-06:00
draft: false
weight: 1
---

# overview
EF Core uses LINQ to query data from the database.

# loading all data
```cs
using var context = new BloggingContext();

var blogs = context.Blogs.ToList();
```

# loading a single entity
```cs
using var context = new BloggingContext();

var blog = context.Blogs.Single(b => b.BlogId == 1);
```

# filtering
```cs
using var context = new BloggingContext();

var blogs = context.Blogs.Where(b => b.Url.Contains("dotnet"))
                                          .ToList();
```
