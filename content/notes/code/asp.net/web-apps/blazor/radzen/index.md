---
title: "notes > code > asp.net > web apps > blazor > radzen"
date: 2023-06-12T00:00:00-06:00
draft: false
---

# Overview
Radzen Blazor Components — a set of free Blazor UI components.

https://blazor.radzen.com/get-started  

https://blazor.radzen.com/docs/guides/getting-started  

# Installation
```powershell
dotnet add package Radzen.Blazor
```

# Getting Started
## 1. Add Imports
`_Imports.razor`
```html
@using Radzen
@using Radzen.Blazor
```

## 2. Add a Theme
`Pages/_Host.cshtml` (Blazor Server) or `wwwroot/index.html` (Blazor WASM)
```html
<!-- Other themes are also available -->
<link rel="stylesheet" href="_content/Radzen.Blazor/css/material-base.css">
```

## 3. Add JS Interop
`Pages/_Host.cshtml` (Blazor Server) or `wwwroot/index.html` (Blazor WASM)
```html
<script src="_content/Radzen.Blazor/Radzen.Blazor.js"></script>
```

## 4. Add Components
These Components require special configuration:  

`MainLayout.razor`
```html
<RadzenDialog/>
<RadzenNotification/>
<RadzenContextMenu/>
<RadzenTooltip/>
```

## 5. Register Services
The above Components require service registration:  

```cs
   using Radzen;
    // ...
    public static async Task Main(string[] args)
    {
        var builder = WebAssemblyHostBuilder.CreateDefault(args);
        builder.RootComponents.Add<App>("app");

        builder.Services.AddTransient(sp => new HttpClient { BaseAddress = new Uri(builder.HostEnvironment.BaseAddress) });

        // ...

        builder.Services.AddScoped<DialogService>();
        builder.Services.AddScoped<NotificationService>();
        builder.Services.AddScoped<TooltipService>();
        builder.Services.AddScoped<ContextMenuService>();
        // ...

        await builder.Build().RunAsync();
    }
```