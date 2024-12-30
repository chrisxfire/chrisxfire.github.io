---
title: static files
date: 2023-04-18T00:00:00-06:00
draft: false
weight: 1
---

# overview
Serve static assets by calling `UseStaticFiles` in the request processing pipeline.

# Static Files in Non-Development Environments
Static assets are only enabled by default in the Development environment.  In other environments, call `UseStaticWebAssets` on the `WebApplicationBuilder`:  
`Program.cs`
```cs
if (builder.Environment.IsStaging())
{
    builder.WebHost.UseStaticWebAssets();
}
```

# [File Mappings and Static File Options](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/static-files?view=aspnetcore-7.0#blazor-server-file-mappings-and-static-file-options)
