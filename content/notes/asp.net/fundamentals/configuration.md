---
title: configuration
date: 2023-08-17T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-7.0

Configuration consists of *host* and *app* configuration providers.  The `WebApplicationBuilder` contains the host:
```cs
var builder = WebApplication.CreateBuilder(args);
```

See also: [Configuration in .NET](../../../_net/configuration/overview)

# Concepts
## Host Configuration
Host configuration providers in order of priority for `WebApplicationBuilder`:
1. Command line arguments
2. DOTNET_-prefixed environment variables
3. ASPNETCORE_-prefixed environment variables

Host configuration providers in order of priority for the .NET Generic Host and Web Host (deprecated):
- ASPNETCORE_-prefixed environment variables
- Command-line arguments
- DOTNET_-prefixed environment variables

### Host variables
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-7.0#host-variables

## App Configuration
App configuration providers in order of priority:
1. Command line arguments
2. Non-prefixed environment variables
3. User secrets if app is running in `Development` environment
4. `appsettings.ENVIRONMENT.json` (JSON configuration provider)
5. A fallback to host configuration

- For confidential configuration data, use [Secret Manager](https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets?view=aspnetcore-6.0#secret-manager).  
- For production secrets, use [Azure Key Vault](https://docs.microsoft.com/en-us/aspnet/core/security/key-vault-configuration?view=aspnetcore-6.0).

## Configuration Providers
Both the host and the app are configured using these configuration providers.  Any host-specific configuration key-value pairs are also included in the app's configuration.

### JSON Configuration Provider
By default, the JSON configuration provider is configured to:
- Search for `appsettings.json` and then `appsettings.ENVIRONMENT.json` 
- Set `reloadOnChange` to `true`

Use the JSON configuration provider like this:
```cs
var builder = WebApplication.CreateBuilder(args);

// If using a configuration file other than appsettings.ENVIRONMENT.json:
builder.Configuration.AddJsonFile("MyConfig.json",
        optional: true,
        reloadOnChange: true);

builder.Services.Configure<SomeOptions>(
    builder.Configuration.GetSection(SomeOptions.Section));

builder.Services.AddRazorPages();

var app = builder.Build();
```

### Non-prefixed Environment Variables Configuration Provider
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-7.0#non-prefixed-environment-variables

### Command Line Configuration Provider
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-7.0#command-line

### Other Configuration Providers
> INI files: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-7.0#ini-configuration-provider  
> XML files: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-7.0#xml-configuration-provider  
> Key-per file: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-7.0#key-per-file-configuration-provider  
> Memory: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-7.0#memory-configuration-provider

## Connection String Prefixes
The Configuration API has special rules for some connection string environment variables.

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-7.0#connection-string-prefixes

## Kestrel Endpoint Configuration
Configuration for Kestrel provided in `appsettings.json` **overrides all cross-server endpoint configurations.**
- This includes command line arguments.

## Adding Configuration from an External Assembly
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/platform-specific-configuration?view=aspnetcore-7.0

## Adding Configuration via Extension Methods
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-7.0#combining-service-collection

## Adding Configuration with a Delegate
Options configured in a delegate override the values set in the configuration providers.

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-7.0#configure-options-with-a-delegate

# Accessing Configuration
## `ConfigurationBinder.GetValue`
`ConfigurationBinder` has extension methods for `IConfiguration`.  Use to access a single value from configuration:
```cs
public class SomeClass 
{
    private readonly IConfiguration _config;

    public SomeClass(IConfiguration config) 
    {
        _config = config;
    }

    public void SomeMethod()
    {
        var value = _config.GetValue<int>("KEY", 0); // if KEY is not found, use the default value of 0
    }
}
``` 

## `IConfiguration.GetSection`
Use to access a configuration section (`IConfigurationSection`):
```cs
public class SomeClass 
{
    private readonly IConfiguration _configSection;

    public SomeClass(IConfiguration config) 
    {
        // If a matching section is not found, GetSection returns an empty IConfigurationSection.
        _configSection = config.GetSection("SectionName");
        // or...
        _configSection = config.GetSection("Section:SubSection");
    }

    public void SomeMethod() 
    {
        Console.WriteLine(_configSection["KEY"]);
    }
}
```

## `IConfiguration.GetChildren`
Use to access a configuration section (`IConfigurationSection`) and its children:
```cs
private readonly IConfiguration _config;

public SomeClass(IConfiguration config) 
{
    _config = config;
}

public void SomeMethod()
{
    var configGroup = _config.GetSection("SectionName");

    if (!configGroup.Exists()) 
    {
        throw new Exception("No such configuration section");
    }

    var children = configGroup.GetChildren();

    foreach (var child in children)
    {
        var key = child.Key;
        var value = child[key];
    }
}
```

## Accessing Configuration in `Program.cs`
`appsettings.json`
```json
{
  ...
  "KeyOne": "Key One Value",
  "KeyTwo": 1999,
  "KeyThree": true
}
```

`Program.cs`
```cs
var builder = WebApplication.CreateBuilder(args);

var key1 = builder.Configuration.GetValue<string>("KeyOne");

var app = builder.Build();

app.MapGet("/", () => "Hello World!");

var key2 = app.Configuration.GetValue<int>("KeyTwo");
var key3 = app.Configuration.GetValue<bool>("KeyThree");

app.Logger.LogInformation("KeyOne: {KeyOne}", key1);
app.Logger.LogInformation("KeyTwo: {KeyTwo}", key2);
app.Logger.LogInformation("KeyThree: {KeyThree}", key3);

app.Run();
```

# Other Configuration
Other configuration includes configuration for the development environment (ie: `launch.json` / `launchSettings.json` and `web.config`)

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-7.0#other-configuration