---
title: configuration
date: 2023-04-17T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Blazor WASM loads configuration from these files by default:
- `wwwroot/appsettings.json`
- `wwwroot/appsettings.{ENVIRONMENT}.json`

To read configuration files other than these, use an `HttpClient.`

# Important Notes
- Configuration and settings files in Blazor WASM apps are visible to end users.
- Do not use these configuration providers in Blazor WASM:
    - Azure Key Vault (the client secret cannot be secured client-side)
    - Azure App (Blazor WASM apps don't run on the server)
- Logging configuration, even if in one of these files, is not loaded by default.

# Using Configuration Data
Inject an `IConfiguration` instance into a component:
```html
@page "/configuration-example"
@using Microsoft.Extensions.Configuration
@inject IConfiguration Configuration

<h1 style="font-size:@Configuration["h1FontSize"]">
    Configuration example
</h1>
```

# Memory Configuration Source
In `Program.cs`:
```cs
using Microsoft.Extensions.Configuration.Memory;

var vehicleData = new Dictionary<string, string>()
{
    { "color", "blue" },
    { "type", "car" },
    { "wheels:count", "3" },
    { "wheels:brand", "Blazin" },
    { "wheels:brand:type", "rally" },
    { "wheels:year", "2008" },
};

var memoryConfig = new MemoryConfigurationSource { InitialData = vehicleData };

builder.Configuration.Add(memoryConfig);
```

To access the memory configuration source, in `Pages/MemoryConfig.razor`:
```html
@page "/memory-config"
@using Microsoft.Extensions.Configuration
@inject IConfiguration Configuration

<h1>Memory configuration example</h1>

<h2>General specifications</h2>

<ul>
    <li>Color: @Configuration["color"]</li>
    <li>Type: @Configuration["type"]</li>
</ul>

<h2>Wheels</h2>

<ul>
    <li>Count: @Configuration["wheels:count"]</li>
    <li>Brand: @Configuration["wheels:brand"]</li>
    <li>Type: @Configuration["wheels:brand:type"]</li>
    <li>Year: @Configuration["wheels:year"]</li>
</ul>
```
To get just the wheels section of this sample configuration:
```cs
@code {
    protected override void OnInitialized()
    {
        var wheelsSection = Configuration.GetSection("wheels");

        ...
    }
}
```

# Authentication Configuration
Provide auth configuration like normal, for example in `wwwroot/appsettings.json`:
```json
{
  "Local": {
    "Authority": "{AUTHORITY}",
    "ClientId": "{CLIENT ID}"
  }
}
```
Load the configuration in `Program.cs`:
```cs
builder.Services.AddOidcAuthentication(options =>
    builder.Configuration.Bind("Local", options.ProviderOptions));
```

# Logging Configuration
First, add `Microsoft.Extensions.Logging.Configuration` to the app.  
Then, in `Program.cs`:
```cs
builder.Logging.AddConfiguration(
    builder.Configuration.GetSection("Logging"));
```

# Using Configuration in HostBuilder
You can read configuration from `WebAssemblyHostBuilder.Configuration` in `Program.cs`:
```cs
var hostname = builder.Configuration["HostName"];
```

# Using Options Configuration
First, add `Microsoft.Extensions.Options.ConfigurationExtensions` to the app.  
Then, in `Program.cs`:
```cs
builder.Services.Configure<MyOptions>(
    builder.Configuration.GetSection("MyOptions"));
```
Note:  In Razor components, `IOptionsSnapshot<TOptions>` and `IOptionsMonitor<TOptions>` is supported, but calling `StateHasChanged` does not update snapshot or monitored option values.  The app must be reopened in a new browser tab or reloaded via the browser's reload button.
