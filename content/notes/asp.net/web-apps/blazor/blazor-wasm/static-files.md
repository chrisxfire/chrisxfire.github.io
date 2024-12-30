---
title: static files
date: 2023-04-18T00:00:00-06:00
draft: false
weight: 1
---

# overview
For the Server app of a hosted Blazor WASM solution, configure static file middleware by calling `UseStaticFiles` in the request processing pipeline.

# static web asset base path
By default, publishing a Blazor WASM app publishes the app's static assets at the root path of the published output.  This is configurable with `<StaticWebAssetBasePath>`:

`project.csproj`
```xml
<PropertyGroup>
    <StaticWebAssetBasePath>{PATH}</StaticWebAssetBasePath>
</PropertyGroup>
```

# scenarios
## client project of hosted blazor wasm app
- `<StaticWebAssetBasePath>` not set
  - Client app is published at `/BlazorHostedSample/Server/bin/Release/{TFM}/publish/wwwroot/`
- `<StaticWebAssetBasePath>` set to `app1`
  - Client app is published at `/BlazorHostedSample/Server/bin/Release/{TFM}/publish/wwwroot/app1/`
## standalone blazor wasm app
- `<StaticWebAssetBasePath>` not set
  - App is published at `/BlazorStandaloneSample/bin/Release/{TFM}/publish/wwwroot/`
- `<StaticWebAssetBasePath>` set to `app1`
  - App is published at `/BlazorStandaloneSample/bin/Release/{TFM}/publish/wwwroot/app1/`
			

