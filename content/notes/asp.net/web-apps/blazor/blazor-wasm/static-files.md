---
title: "notes > asp.net > web apps > blazor > blazor wasm > static files"
date: 2023-04-18T00:00:00-06:00
draft: false
---

# Overview
For the Server app of a hosted Blazor WASM solution, configure static file middleware by calling `UseStaticFiles` in the request processing pipeline.

# Static Web Asset Base Path
By default, publishing a Blazor WASM app publishes the app's static assets at the root path of the published output.  This is configurable with `<StaticWebAssetBasePath>`:

`project.csproj`
```xml
<PropertyGroup>
    <StaticWebAssetBasePath>{PATH}</StaticWebAssetBasePath>
</PropertyGroup>
```

# Scenarios
## Client project of hosted Blazor WASM app
- `<StaticWebAssetBasePath>` not set
  - Client app is published at `/BlazorHostedSample/Server/bin/Release/{TFM}/publish/wwwroot/`
- `<StaticWebAssetBasePath>` set to `app1`
  - Client app is published at `/BlazorHostedSample/Server/bin/Release/{TFM}/publish/wwwroot/app1/`
## Standalone Blazor WASM app
- `<StaticWebAssetBasePath>` not set
  - App is published at `/BlazorStandaloneSample/bin/Release/{TFM}/publish/wwwroot/`
- `<StaticWebAssetBasePath>` set to `app1`
  - App is published at `/BlazorStandaloneSample/bin/Release/{TFM}/publish/wwwroot/app1/`
			

