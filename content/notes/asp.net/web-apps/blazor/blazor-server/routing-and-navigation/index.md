---
title: notes > asp.net > web apps > blazor > blazor server > routing and navigation
date: 2023-04-17T00:00:00-06:00
draft: false
---

# ASP.NET Core Endpoint Routing Integration
Blazor Server integrates with ASP.NET Core endpoint routing via `MapBlazorHub`:
```cs
app.UseRouting();

app.MapBlazorHub();
app.MapFallbackToPage("/_Host");
```
