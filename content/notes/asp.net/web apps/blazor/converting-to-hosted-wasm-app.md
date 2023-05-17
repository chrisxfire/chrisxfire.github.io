---
title: "notes > asp.net > web apps > blazor > converting to hosted WASM app"
date: 2023-05-01T00:00:00-06:00
draft: false
---

# Overview
The existing solution contains:
- BethanysPieShopHRM.Api
- BethanysPieShopHRM.App
- BethanysPieShopHRM.Shared

Presently, BethanysPieShopHRM.App is a *standalone* Blazor WASM app.  
This process converts it to a *hosted* Blazor WASM app.

# BethanysPieShopHRM.Api
1. `dotnet add package Microsoft.AspNetCore.Components.WebAssembly.Server`

2. `Program.cs`
    ```cs
    // ...
    if (app.Environment.IsDevelopment())
    {
        app.UseWebAssemblyDebugging();
    }

    app.UseBlazorFrameworkFiles(); // needed to serve the app
    app.UseStaticFiles(); // the Blazor app will be hosted as static files
    // ...
    // if an incoming request cannot be routed, re-route it to index.html:
    app.MapFallbackToFile("index.html");
    ```

3. `Properties/launchSettings.json`
    ```json
    "profiles": {
        "BethanysPieShopHRM.Api": {
            // ...
            // remove launchUrl line
            // add this line:
            "inspectUri": "{wsProtocol}://{url.hostname}:{url.port}/_framework/debug/ws-proxy?browser={browserInspectUri}",
            // ...
        },
        "IIS Express": {
            // ...
            "inspectUri": "{wsProtocol}://{url.hostname}:{url.port}/_framework/debug/ws-proxy?browser={browserInspectUri}",
        }
    }
    ```
4. Add a project reference froom `BethanysPieShopHRM.Api` to `BethanysPieShopHRM.App`

