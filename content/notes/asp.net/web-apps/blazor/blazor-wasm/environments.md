---
title: environments
date: 2023-04-18T00:00:00-06:00
draft: false
weight: 1
---

# overview
These notes are specific to Blazor WASM because Blazor Server uses environment configuration of ASP.NET Core.

When run locally, app defaults to Development.  
When app is published, app defaults to Production.  
In a hosted Blazor WASM solution, the Server app sets the `Blazor-Environment` variable to its value.  The Client app reads it and sets the environment when `WebAssemblyHost` is created in `Program.cs`.

# set environment via blazor start configuration
In `wwwroot/index.html` inside the closing `</body>` tag:
```html
<script src="_framework/blazor.webassembly.js" autostart="false"></script>
<script>
  if (window.location.hostname.includes("localhost")) {
    Blazor.start({
      environment: "Staging"
    });
  } else {
    Blazor.start({
      environment: "Production"
    });
  }
</script>
```

This overrides the Blazor-Environment header.

# set environment via environment header
For IIS, in `web.config`:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
  <system.webServer>
    ...
    <httpProtocol>
      <customHeaders>
        <add name="Blazor-Environment" value="Staging" />
      </customHeaders>
    </httpProtocol>
  </system.webServer>
</configuration>
```

# read the environment in a component
Inject `IWebAssemblyHostEnvironment` and read the `Environment` property:  
`Pages/ReadEnvironment.razor`
```html
@page "/read-environment"
@using Microsoft.AspNetCore.Components.WebAssembly.Hosting
@inject IWebAssemblyHostEnvironment HostEnvironment

<h1>Environment example</h1>

<p>Environment: @HostEnvironment.Environment</p>
```

Or, during startup, in `Program.cs`:
```cs
if (builder.HostEnvironment.Environment == "Custom")
{
    ...
};
```

`WebAssemblyHostEnvironmentExtensions` contains `IsDevelopment`, `IsStaging`, `IsProduction`, and `IsEnvironment("environment-name")`.
