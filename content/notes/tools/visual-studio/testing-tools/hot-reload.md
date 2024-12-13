---
title: hot reload
date: 2023-10-01T00:00:00-06:00
draft: false
weight: 1
---

# [Overview](https://learn.microsoft.com/en-us/aspnet/core/test/hot-reload?view=aspnetcore-7.0)  
> [!IMPORTANT]
> Availability: ASP.NET Core 6+

.NET Hot Reload applies code changes (including changes to style sheets) to running apps without restarting and losing state. It is designed for use with ASP.NET Core apps.

# Enabling
via CLI: `dotnet watch`  
`Ctrl`+`R` to force reload

When an unsupported edit (a *rude* edit) is made, dotnet watch asks if you want to restart the app.

# Disabling
via CLI: `dotnet watch --no-hot-reload`  

via `Properties/launchSettings.json`:
```json
"hotReloadEnabled": false
```