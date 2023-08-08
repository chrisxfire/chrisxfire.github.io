---
title: routing
date: 2023-05-03T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Routing in Razor Pages is file-based.  URLs are routed to pages based on their location in the filesystem:
| URL                         | Path                      |
| --------------------------- | ------------------------- |
| / or /Index                 | `/Pages/Index.cshtml`       |
| /Contact                    | `/Pages/Contact.cshtml`     |
| /Store or /Store/Index.html | `/Pages/Store/Index.cshtml` |

| URL                            | Maps to this Razor page      |
| ------------------------------ | ---------------------------- |
| www.example.com                 | `Pages/Index.cshtml`           |
| www.example.com/index           | `Pages/Index.cshtml`           |
| www.example.com/products        | `Pages/Products/Index.cshtml`  |
| www.example.com/products/create | `Pages/Products/Create.cshtml` |
