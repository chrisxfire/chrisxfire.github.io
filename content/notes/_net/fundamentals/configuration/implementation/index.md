---
title: notes > .net > fundamentals > configuration > implementation
date: 2022-08-23T17:15:19-0600
draft: false
---
# Example
Install packages:
`dotnet add package microsoft.extensions.configuration`
`dotnet add package microsoft.extensions.configuration.json`
`dotnet add package microsoft.extensions.configuration.binder`
`dotnet add package microsoft.extensions.configuration.environmentvariables` # Only if using environment variables.

Assuming this appsettings.json file:
`{`
`"Settings": {`
`"KeyOne": 1,`
`"KeyTwo": true,`
`"KeyThree": {`
`"Message": "Oh, that's nice..."`
`}`
`}`
`}`

Set the file properties:
- `Build action` = `Content`
- `Copy to Output Directory` = `Copy always` or `Copy if newer`

// Assuming this code for settings object:
```cs
public class Settings
{
    public int KeyOne { get; set; }
    public bool KeyTwo { get; set; }
    public NestedSettings KeyThree { get; set; } = null!;
}

public class NestedSettings
{
    public string Message { get; set; } = null!;
}
```
## [Hosted Approach](https://docs.microsoft.com/en-us/dotnet/core/extensions/configuration#basic-example-with-hosting)
```cs
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Hosting;

using IHost host = Host.CreateDefaultBuilder(args).Build();

// Ask the service provider for the configuration abstraction:
IConfiguration config = host.Services.GetRequiredService<IConfiguration>();

// Get values from the config given their key and their target type.
int keyOneValue = config.GetValue<int>("KeyOne");
bool keyTwoValue = config.GetValue<bool>("KeyTwo");
string keyThreeNestedValue = config.GetValue<string>("KeyThree:Message");

// Write the values to the console.
Console.WriteLine($"KeyOne = {keyOneValue}");
Console.WriteLine($"KeyTwo = {keyTwoValue}");
Console.WriteLine($"KeyThree:Message = {keyThreeNestedValue}");

// Application code which might rely on the config could start here.

await host.RunAsync();
```
## Non-Hosted Approach
```cs
using Microsoft.Extensions.Configuration;

// Build a config object, using env vars and JSON providers:
IConfiguration config = new ConfigurationBuilder()
    .AddJsonFile("appsettings.json")
    .AddEnvironmentVariables()
    .Build();

// Get values from the config given their key and their target type:
Settings settings = config.GetRequiredSection("Settings").Get<Settings>();

// Write the values to the console.
Console.WriteLine($"{settings.KeyOne}"); // 1
Console.WriteLine($"{settings.KeyTwo}"); // True
Console.WriteLine($"{settings.KeyThree.Message}"); // "Oh, that's nice…"

// Application code which might rely on the config could start here.
```
