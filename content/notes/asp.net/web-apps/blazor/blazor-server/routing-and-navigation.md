---
title: routing and navigation
date: 2023-04-17T00:00:00-06:00
draft: false
weight: 1
---

# [ASP.NET Core Endpoint Routing Integration](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/routing?view=aspnetcore-7.0#aspnet-core-endpoint-routing-integration)
Blazor Server integrates with ASP.NET Core endpoint routing via `MapBlazorHub`:
```cs
app.UseRouting();

app.MapBlazorHub();
app.MapFallbackToPage("/_Host");
```
