---
title: options pattern
date: 2022-08-23T17:16:31-0600
draft: false
weight: 1
---
# [Overview](https://learn.microsoft.com/en-us/dotnet/core/extensions/options)
The Configuration Options pattern uses classes to provide access to strongly-typed groups of related settings.

This supports two software engineering principles:
1.  Interface Segregation Principle (or Encapsulation): Classes that depend on configuration settings depend only on the configuration settings that they use.
2.  Separation of Concerns: Settings for different parts of the app are not dependent or coupled with one another.
# 
`appsettings.json`:
```json
"Units": 
{
    "Temp": "Celsius",
    "Distance": "Miles"
}
```

`UnitOptions.cs`:
Note: This (or any) Options class must:
- Be a concrete class
- Have a public, parameterless constructor
- Contain public read-write properties to bind (fields are not bound)

```cs
public class UnitOptions
{
    public string Temp { get; set; } = String.Empty;
    public string Distance { get; set; } = String.Empty;
}
```

`Program.cs`:
```cs
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.Options;

…
// Register the validator with the DI container:
builder.Services.AddSingleton<IValidator<UnitOptions>, UnitOptionsValidator>();

builder.Services.AddOptions<UnitOptions>() // For the UnitOptions type…
    .BindConfiguration(nameof(UnitOptions)) // …bind the "UnitOptions" section of the configuration file…
    .ValidateDataAnnotations() // …enable validation of any annotations…
    .ValidateOnStart() // …and validate on app startup.

// Register the UnitOptions object with the DI container by delegating to the IOptions object.
// This allows you to avoid the dependency on IOptions in your classes:
builder.Services.AddSingleton(resolver => resolver.GetRequiredService<IOptions<UnitOptions>>().Value);

// Add the service to the DI container:
builder.Services.AddTransient<ISomeService, SomeService>();
…
```
# Injecting Options
`SomeService.cs`:
```cs
public interface ISomeService
{
    UnitOptions GetUnits();
}

public class SomeService: ISomeService
{
    private readonly UnitOptions _unitOptions;

    // Inject UnitOptions from the DI container:
    public SomeService(IOptions<UnitOptions> unitOptions)
    {
        _unitOptions = unitOptions.Value;
    }
    public UnitOptions GetUnits()
    {
        return _unitOptions;
    }
}
```
# Validating Options
`Validator.cs`:
```cs
public class UnitOptionsValidator : IValidateOptions<UnitOptions>
{
    public UnitOptionsValidator()
    {
    }

    public ValidateOptionsResult Validate(UnitOptions options)
    {
        ArgumentNullException.ThrowIfNull(options);

        // Perform validation:
        // …
        // If a validation fails:
        ValidateOptionsResult.Fail("failure message");

        return ValidateOptionsResult.Success;
    }
}
```
# Interfaces
## `IOptions<TOptions>`
- Is registered as a Singleton and can be injected into any service lifetime.
- Does not support reading changes from the JSON configuration file after the app started.
- Does not support named options.

## `IOptionsSnapshot<TOptions>`
- Is registered as Scoped and cannot be injected into a Singleton service.
- Use if options should be re-read after every injection resolution in Scoped or Transient lifetimes.
- Supports named options.

## `IOptionsMonitor<TOptions>`
- Is registered as a Singleton.
- Use to read options and manage options notifications.
- Supports change notifications, named options, reloadable configuration, select options validation.

# Using Named Options
<https://docs.microsoft.com/en-us/dotnet/core/extensions/options#named-options-support-using-iconfigurenamedoptions>
