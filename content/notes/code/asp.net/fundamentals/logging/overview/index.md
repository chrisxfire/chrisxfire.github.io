---
title: notes > code > asp.net > fundamentals > logging > overview
date: 2023-01-13T00:00:00-06:00
draft: false
weight: -1
---

# Overview
See also:  
- [Logging in .NET Core and ASP.NET Core | Microsoft Learn](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/logging/?view=aspnetcore-7.0)
- [HTTP Logging in .NET Core and ASP.NET Core | Microsoft Learn](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/http-logging/?view=aspnetcore-7.0)
- [W3CLogger in .NET Core and ASP.NET Core | Microsoft Learn](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/w3c-logger/?view=aspnetcore-7.0)

ASP.NET Core supports logging with built-in and third-party logging providers:  Console, Debug, Event Tracing, Windows Event Log, TraceSource, Azure App Service, Azure Application Insights.

To create logs, resolve an `ILogger<TCategoryName>` service from DI and call logging methods like LogInformation:
```cs
public class SomeClass {
    private readonly ILogger<SomeClass> _logger;
    
    public SomeMethod(Context context, ILogger<SomeClass> logger) {
        _context = conetxt;
        _logger = logger;
    }
    
    public async Task OnGetAsync() {
        _logger.LogInformation("SomeClass OnGetAsync.");
    }
}
```
