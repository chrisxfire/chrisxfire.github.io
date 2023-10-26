---
title: options pattern
date: 2023-09-20T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/dotnet/core/extensions/options

The options pattern uses classes to provide strongly-typed access to groups of related settings. It uses configuration files like [configuration in .NET](../overview).

This pattern supports a mechanism to validate configuration data.

# Configuring and Using Options
High-level Process:  
1. Create options classes that model the configuration data
2. Add instances of `Option<TOption>` to the DI container
3. Inject the `Option<TOption>` instances into classes that need them

## 1. Create Options Classes
Options classes must:
1. Be non-abstract
2. Have a public, parameterless constructor
3. Contain public, read-write properties to bind (fields are **not** bound)

See [notes on Configuration](../implementation) for an example of how to model a class after JSON-based configuration.

## 2. Add Options to DI Container
`appsettings.json`
```json {hl_lines=[3-6]}
{
    "SecretKey": "Secret key value",
    "SomeOptions": {
        "Enabled": true,
        "AutoRetryDelay": "00:00:07"
    },
    "Logging": {
        "LogLevel": {
            "Default": "Information",
            "Microsoft": "Warning",
            "Microsoft.Hosting.Lifetime": "Information"
        }
    }
}
```
```cs
HostApplicationBuilder builder = Host.CreateApplicationBuilder(args);

builder.Services.Configure<SomeOptions>(builder.Configuration.GetSection(key: nameof(SomeOptions)));
```

## 3. Inject Options into Classes
```cs
using Microsoft.Extensions.Options;

namespace ConsoleJson.Example;

public sealed class ExampleService
{
    private readonly SomeOptions _options;

    public ExampleService(IOptions<SomeOptions> options) =>
        _options = options.Value;

    public void DisplayValues()
    {
        Console.WriteLine($"SomeOptions.Enabled={_options.Enabled}");
        Console.WriteLine($"SomeOptions.AutoRetryDelay={_options.AutoRetryDelay}");
    }
}
```

# Other Ways to Configure Options
## Using `Configuration.GetSection`
```cs
SomeOptions options = new();

builder.Configuration.GetSection(nameof(SomeOptions)) // returns the configuration section
                     .Bind(options);                  // binds the configuration section to the options object

Console.WriteLine($"SomeOptions.Enabled={options.Enabled}");
Console.WriteLine($"SomeOptions.AutoRetryDelay={options.AutoRetryDelay}");
```

## Using `Configuration.Get`
```cs
var options =
    builder.Configuration.GetSection(nameof(SomeOptions)) // returns the configuration section
                         .Get<SomeOptions>();             // binds the configuration section to the options object and
                                                          // returns the object.

Console.WriteLine($"SomeOptions.Enabled={options.Enabled}");
Console.WriteLine($"SomeOptions.AutoRetryDelay={options.AutoRetryDelay}");
```

# Options Interfaces
| Interface             | Can read config data after app starts | Supports named options | Service lifetime |              
| --------------------- | ------------------------------------- | ---------------------- | ---------------- | 
| `IOptions<T>`         | No                                    | Yes                    | Singleton        | 
| `IOptionsSnapshot<T>` | Yes                                   | Yes                    | Scoped           |
| `IOptionsMonitor<T>`  | Yes                                   | Yes                    | Singleton        | 

## `IOptionsSnapshot<T>` vs `IOptionsMonitor<T>`
Use `IOptionsSnapshot` to read updated configuration data. With this interface, options are computed once per request when accessed and are cached for the lifetime of the request. 

`IOptionsSnapshot` is a scoped service and provides a snapshot of the options at the time the object is constructed. It is designed for use with transient and scoped dependencies.

`IOptionsMonitor` is a singleton service that retrieves the current option values at any time. It is designed for use with singleton dependencies.

### Using `IOptionsMonitor<T>`
```cs
using Microsoft.Extensions.Options;

namespace ConsoleJson.Example;

public sealed class MonitorService
{
    private readonly IOptionsMonitor<SomeOptions> _monitor;

    public MonitorService(IOptionsMonitor<SomeOptions> monitor) =>
        _monitor = monitor;

    public void DisplayValues()
    {
        SomeOptions options = _monitor.CurrentValue;

        Console.WriteLine($"SomeOptions.Enabled={options.Enabled}");
        Console.WriteLine($"SomeOptions.AutoRetryDelay={options.AutoRetryDelay}");
    }
}
```

# Named Options
Use named options when multiple configuration sections bind to the same properties. Consider:
`appsettings.json`  
```json
{
  "Features": {
    "Personalize": {
      "Enabled": true,
      "ApiKey": "aGEgaGEgeW91IHRob3VnaHQgdGhhdCB3YXMgcmVhbGx5IHNvbWV0aGluZw=="
    },
    "WeatherStation": {
      "Enabled": true,
      "ApiKey": "QXJlIHlvdSBhdHRlbXB0aW5nIHRvIGhhY2sgdXM/"
    }
  }
}
```

Notice how both `Personalize` and `WeatherStation` have properties of the same name. Instead of creating two classes to bind the options, this class can be used for both sections:
```cs
 public class Features
{
    public const string Personalize = nameof(Personalize);
    public const string WeatherStation = nameof(WeatherStation);

    public bool Enabled { get; set; }
    public string ApiKey { get; set; }
}
```

## Configuring Named Options
```cs
HostApplicationBuilder builder = Host.CreateApplicationBuilder(args);

// Omitted for brevity...

builder.Services.Configure<Features>(Features.Personalize,
                                     builder.Configuration.GetSection("Features:Personalize"));

builder.Services.Configure<Features>(Features.WeatherStation,
                                     builder.Configuration.GetSection("Features:WeatherStation"));
```

## Using Named Options
```cs
public class sealed Service
{
    private readonly Features _personalizeFeature;
    private readonly Features _weatherStationFeature;

    public Service(IOptionsSnapshot<Features> namedOptionsAccessor)
    {
        _personalizeFeature = namedOptionsAccessor.Get(Features.Personalize);
        _weatherStationFeature = namedOptionsAccessor.Get(Features.WeatherStation);
    }
}
```

# Options Validation
Options can be validated with `System.ComponentModel.DataAnnotations`. 

By default, validation is performed the first time an options instance is created. Validation can be performed eagerly (see notes in step 3).

High-level Process:  
1. Annotate the options model with the appropriate data annotations
2. Add support for options validation
3. Enable validation

## 1. Annotate the Options Model
Consider this configuration file:
```json
{
  "MyConfig": {
    "Key1": "My Key One",
    "Key2": 10,
    "Key3": 32
  }
}
```

Here is the model:
```cs
using System.ComponentModel.DataAnnotations;

public class MyConfigOptions
{
    public const string MyConfig = "MyConfig";

    [RegularExpression(@"^[a-zA-Z''-'\s]{1,40}$")]
    public string Key1 { get; set; }
    [Range(0, 1000, ErrorMessage = "Value for {0} must be between {1} and {2}.")]
    public int Key2 { get; set; }
    public int Key3 { get; set; }
}
```

## 2. Add Support for Options Validation
Note: this package is already included in web apps:  
```powershell
dotnet add package Microsoft.Extensions.Options.DataAnnotations 
```

## 3. Enable Validation
```cs
using Microsoft.Extensions.Options.DataAnnotations; // not required for web apps

builder.Services.AddOptions<SomeOptions>()
                .Bind(Configuration.GetSection(nameof(SomeOptions)))
                .ValidateDataAnnotations();
              //.ValidateOnStart(); <-- Optionally, validate eagerly
```

## Validation Sample
A sample class that displays the configuration values or the validation errors:
```cs
using Microsoft.Extensions.Logging;
using Microsoft.Extensions.Options;

namespace ConsoleJson.Example;

public sealed class ValidationService
{
    private readonly ILogger<ValidationService> _logger;
    private readonly IOptions<MyConfigOptions> _config;

    public ValidationService(ILogger<ValidationService> logger, IOptions<MyConfigOptions> config)
    {
        _config = config;
        _logger = logger;

        try
        {
            MyConfigOptions options = _config.Value;
        }
        catch (OptionsValidationException ex)
        {
            foreach (string failure in ex.Failures)
            {
                _logger.LogError(failure);
            }
        }
    }
}
```

Or, perform complex validation using a delegate:
```cs
builder.Services
    .AddOptions<MyConfigOptions>()
    .Bind(Configuration.GetSection(MyConfigOptions.MyConfig))
    .ValidateDataAnnotations()
    .Validate(config =>
    {
        if (config.Scale != 0)
        {
            // Validate must return true if validation succeeds, false otherwise
            return config.VerbosityLevel > config.Scale;
        }

        return true;
    }, "VerbosityLevel must be > than Scale."); // the error message
```

## Complex Validation with `IValidateOptions<T>`
For complex validation scenarios, use `IValidateOptions<TOptions>`:
```cs
using System.Text;
using System.Text.RegularExpressions;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.Options;

namespace ConsoleJson.Example;

sealed partial class ValidateMyConfigOptions : IValidateOptions<MyConfigOptions>
{
    public MyConfigOptions? _settings { get; private set; }

    public ValidateMyConfigOptions(IConfiguration config) =>
        _settings = config.GetSection(MyConfigOptions.MyConfig)
                          .Get<MyConfigOptions>();

    public ValidateOptionsResult Validate(string? name, MyConfigOptions options)
    {
        StringBuilder? failure = null;
    
        if (!ValidationRegex().IsMatch(options.SiteTitle))
            (failure ??= new()).AppendLine($"{options.SiteTitle} doesn't match RegEx");

        if (options.Scale is < 0 or > 1_000)
            (failure ??= new()).AppendLine($"{options.Scale} isn't within Range 0 - 1000");

        if (_settings is { Scale: 0 } && _settings.VerbosityLevel <= _settings.Scale)
            (failure ??= new()).AppendLine("VerbosityLevel must be > than Scale.");

        return failure is not null ?
            ? ValidateOptionsResult.Fail(failure.ToString())
            : ValidateOptionsResult.Success;
    }

    [GeneratedRegex("^[a-zA-Z''-'\\s]{1,40}$")]
    private static partial Regex ValidationRegex();
}
```

Enable validation when using `IValidateOptions<TOptions>` like this:
```cs
builder.Services.Configure<MyConfigOptions>(builder.Configuration.GetSection(MyConfigOptions.MyConfig));

builder.Services.AddSingleton<IValidateOptions<MyConfigOptions>, MyConfigValidation>();
```

## Complex Validation with `IValidatableObject`
Class-level validation can be performed on the options class itself by:
1. Implementing `IValidatableObject` and its `Validate` method on the class
2. Calling `ValidateDataAnnotations` in `Program.cs`

## Complex Validation with `CustomValidationAttribute`
Mark the member to be validated with `[CustomValidation]` and create a custom validation method: 

When annotating with the `CustomValidation` attribute, its first argument is the type of the validation method that will be used, and its second argument is the name of the validation method that will be used:
```cs {hl_lines=11}
public class MyConfigOptions
{
    public const string MyConfig = "MyConfig";

    [RegularExpression(@"^[a-zA-Z''-'\s]{1,40}$")]
    public string Key1 { get; set; }
    
    [Range(0, 1000, ErrorMessage = "Value for {0} must be between {1} and {2}.")]
    public int Key2 { get; set; }
    
    [CustomValidation(typeof(Validate), nameof(IsKey3NonNegative))]
    public int Key3 { get; set; }
}
```

The custom validation method must:
1. Be public
2. Be static
3. Return ValidationResult
4. Accept a parameter of the same type as the member being validated

```cs {hl_lines=3}
public class Validate 
{
    public static ValidationResult IsKey3NonNegative(int key) 
    {
        return key < 0 
            ? new ValidationResult("key cannot be negative")
            : ValidationResult.Success;
    }
}
```

# Post-configuration
Post-configuration runs after all options configuration occurs. It is useful when you need to override configuration without changing the configuration file itself:
```cs
builder.Services.PostConfigure<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

Or, with named options:
```cs
builder.Services.PostConfigure<CustomOptions>("named_options_1", customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

Or, to post-configure all configuration instances:
```cs
builder.Services.PostConfigureAll<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

# Accessing Options in `Program.cs`
Use GetRequiredService:
```cs
var app = builder.Build();

var option1 = app.Services.GetRequiredService<IOptionsMonitor<MyOptions>>().CurrentValue.Option1;
```