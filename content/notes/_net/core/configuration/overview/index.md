---
title: notes > .net > core > configuration > overview
date: 2021-12-30T14:12:34-0700
draft: false
---
# [Configuraton Providers](https://learn.microsoft.com/en-us/dotnet/core/extensions/configuration-providers)
Configuration providers exist for settings files, environment variables, Azure key vault, Azure app configuration, command-line arguments, custom providers, key-per-file, and in-memory .NET objects.

# Packages
Microsoft.Extensions.Configuration
Microsoft.Extensions.HostingNot required unless using a GenericHost.
[Microsoft.Extensions.Configuration.Binder](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Binder)Bind an object to data in configuration providers.
[Microsoft.Extensions.Configuration.Json](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.Json)JSON configuration provider.
[Microsoft.Extensions.Configuration.EnvironmentVariables](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.EnvironmentVariables)Environment variables provider.

Note: `System.Configuration.ConfigurationBuilder` != `Microsoft.Extensions.Configuration.ConfigurationBuilder`.

# Binding
Configuration values can be bound to instances of .NET objects.

Interfaces:
IConfigurationRepresents a set of key/value configuration properties.
IConfigurationRootThe root of an IConfiguration hierarchy.
IConfigurationSectionA section of configuration values.
# Configuration Provider Priority
1.  Command Line
2.  App Secrets (Secret Manager) in development enviornment
3.  Environment Variables
4.  XML / JSON / INI

This means #1 will override #2 and so on.
# JSON Configuration Provider
```cs
using IHost host = Host.CreateDefaultBuilder(args).ConfigureAppConfiguration((hostingContext, configuration) =>
{
    // Clear all providers that were added from CreateDefaultBuidler():
    configuration.Sources.Clear();

    IHostEnvironment env = hostingContext.HostingEnvironment;

    // *Build Action* must be set to *Content*; *Copy to Output Directory* must be *Copy if newer* or *Always*.
    configuration
    .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
    .AddJsonFile($"appsettings.{env.EnvironmentName}.json", true, true);

    // Get the root of the configuration hierarchy. Sections from the configuration can be bound to .NET
    // objects and provided as IOptions<TOptions> through dependency injection.
    IConfigurationRoot configurationRoot = configuration.Build();

    // This class is for the options in appsettings.json:
    TransientFaultHandlingOptions options = new();
    configurationRoot.GetSection(nameof(TransientFaultHandlingOptions))
    .Bind(options);

    Console.WriteLine($"TransientFaultHandlingOptions.Enabled={options.Enabled}");
    Console.WriteLine($"TransientFaultHandlingOptions.AutoRetryDelay={options.AutoRetryDelay}");
})
.Build();

// Application code should start here.

await host.RunAsync();
```
# Environment Variables Configuration Provider
Same code as above, except:
```cs
configuration.AddEnvironmentVariables();
```

## Prefixes
```cs
// Set a prefix:
configuration.AddEnvironmentVariables(prefix: "CustomPrefix_");
```

## Environment Variable Hierarchical Keys Separator
The `:` separator does not work with environment variable hierarchical keys on all platforms. Use `__` instead.
So, instead of`set TransientFaultHandlingOptions:Enabled="true"`
Use:`set TransientFaultHandlingOptions__Enabled="true"`
Note: Use `setx` to persist the environment variable. Use `setx /M` to make it a system environment variable.

# Command Line Arguments Configuration Provider
Same come as above, except:
```cs
if (args is { Length: > 0})
configuration.AddCommandLine(args);
```

## Sending Command Line Arguments with dotnet
`dotnet run *SomeKey*="*Some value*"`

# INI Configuration Provider
Same code as above, except:
```cs
configruation.AddIniFile(appsettings.ini", optional: true, reloadOnChange: true)
```

# Memory Configuration Provider
```cs
using IHost host = Host.CreateDefaultBuilder(args).ConfigureAppConfiguration((_, configuration) =>
    configuration.AddInmemoryCollection(
        new Dictionary<string, string> {
        ["*SomeKey*"] = "*Some value*",
        ["*SomeOtherKey*:*Enabled*"] = bool.TrueString
    }))
.Build();
```
# Additional Reading
[Safe storage of app secrets in development in ASP.NET Core | Microsoft Docs](https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets?view=aspnetcore-6.0&tabs=windows)
