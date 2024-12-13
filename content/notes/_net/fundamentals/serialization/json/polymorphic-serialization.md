---
title: polymorphic serialization
date: 2023-07-27T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> [!IMPORTANT]
> Availability: .NET 7

- Documentation: https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/polymorphism?pivots=dotnet-7-0

`System.Text.Json` supports polymorphic type hierarchies with these attributes:
- `[JsonDerivedType]` — indicates that the specified subtype should be opted into polymorphic serialization
- `[JsonPolymorphic]` — indicates that the type should be serialized polymorphically

# Serializing Properties of a Derived Class
Consider this base class...
```cs {hl_lines=1}
[JsonDerivedType(typeof(WeatherForecastWithCity))]
public class WeatherForecastBase
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    public string? Summary { get; set; }
}
```

...and this derived class:
```cs
public class WeatherForecastWithCity : WeatherForecastBase
{
    public string? City { get; set; }
}
```

Assume the type argument of `Serialize<T>` at compile time is `WeatherForecastBase`:
```cs
options = new JsonSerializerOptions
{
    WriteIndented = true
};
jsonString = JsonSerializer.Serialize<WeatherForecastBase>(weatherForecastBase, options);
```

The `City` property is serialized because the `weatherForecastBase` object is actually a WeatherForecastWithCity object since we used the `[JsonDerivedType]` attribute:

```json
{
  "City": "Milwaukee",
  "Date": "2022-09-26T00:00:00-05:00",
  "TemperatureCelsius": 15,
  "Summary": "Cool"
}
```

# Deserializing Properties of a Derived Class
To enable polymorphic deserialization, a  type discriminator must be specified for the derived class:
```cs {hl_lines=[1,2]}
[JsonDerivedType(typeof(WeatherForecastBase), typeDiscriminator: "base")]
[JsonDerivedType(typeof(WeatherForecastWithCity), typeDiscriminator: "withCity")]
public class WeatherForecastBase
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    public string? Summary { get; set; }
}

public class WeatherForecastWithCity : WeatherForecastBase
{
    public string? City { get; set; }
}
```

This added metadata allows the serializer to serialize and deserialize the payload as `WeatherForecastWithCity` from its base `WeatherForecastBase` type:
```cs
WeatherForecastBase weather = new WeatherForecastWithCity
{
    City = "Milwaukee",
    Date = new DateTimeOffset(2022, 9, 26, 0, 0, 0, TimeSpan.FromHours(-5)),
    TemperatureCelsius = 15,
    Summary = "Cool"
}
var json = JsonSerializer.Serialize<WeatherForecastBase>(weather, options);
Console.WriteLine(json);
```
Output:
```json
{
  "$type" : "withCity", // this is the type discriminator metadata 
  "City": "Milwaukee",
  "Date": "2022-09-26T00:00:00-05:00",
  "TemperatureCelsius": 15,
  "Summary": "Cool"
}
```

# JsonPolymorphic
The `[JsonPolymorphic]` attribute customizes the type discriminator's name.  The default name is `$type`:
```cs
[JsonPolymorphic(TypeDiscriminatorPropertyName = "$discriminator")]
[JsonDerivedType(typeof(ThreeDimensionalPoint), typeDiscriminator: "3d")]
public class BasePoint
{
    public int X { get; set; }
    public int Y { get; set; }
}

public sealed class ThreeDimensionalPoint : BasePoint
{
    public int Z { get; set; }
}

BasePoint point = new ThreeDimensionalPoint { X = 1, Y = 2, Z = 3 };
var json = JsonSerializer.Serialize<BasePoint>(point);
Console.WriteLine(json);
// Sample output:
//  { "$discriminator": "3d", "X": 1, "Y": 2, "Z": 3 }
```
