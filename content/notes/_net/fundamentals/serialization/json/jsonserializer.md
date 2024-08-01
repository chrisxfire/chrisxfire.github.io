---
title: jsonserializer
date: 2021-11-11T10:57:32-0700
draft: false
weight: 1
---

# Overview [[Documentation](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/how-to?pivots=dotnet-7-0)]  

A high-level, automatic serialization and deserialization API. JsonSerializer's source generator eliminates use of reflection which is important
for trimming and native AOT apps.

# Serializing and Deserializing with JsonSerializer
These examples use the following classes:
```cs {hl_lines=[7,8]}
public class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    public string? Summary { get; set; }
    public string? SummaryField;
    public IList<DateTimeOffset>? DatesAvailable { get; set; }
    public Dictionary<string, HighLowTemps>? TemperatureRanges { get; set; }
    public string[]? SummaryWords { get; set; }
}

public class HighLowTemps
{
    public int High { get; set; }
    public int Low { get; set; }
}
```

## via Custom Types
### Serializing to JSON
This data can be serialized as follows:
```cs
var weatherForecast = new WeatherForecast
{
    Date = DateTime.Parse("2019-08-01"),
    TemperatureCelsius = 25,
    Summary = "Hot",
    SummaryField = "Hot",
    DatesAvailable = new List<DateTimeOffset>() 
        { DateTime.Parse("2019-08-01"), DateTime.Parse("2019-08-02") },
    TemperatureRanges = new Dictionary<string, HighLowTemps>
        {
            ["Cold"] = new HighLowTemps { High = 20, Low = -10 },
            ["Hot"] = new HighLowTemps { High = 60 , Low = 20 }
        },
    SummaryWords = new[] { "Cool", "Windy", "Humid" }
};

var options = new JsonSerializerOptions { WriteIndented = true };
string jsonString = JsonSerializer.Serialize(weatherForecast, options);
```

Output:
```
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": 20,
      "Low": -10
    },
    "Hot": {
    "High": 60,
      "Low": 20
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

The Serialize method has an overload which takes a generic type parameter rather than using type inference:
```cs
string jsonString = JsonSerializer.Serialize<WeatherForecast>(weatherForecast, options);
```

### Serializing to UTF-8
Serializing to a UTF-8 byte array is faster because bytes do not need to be converted to strings (UTF-16):
```cs
byte[] jsonUtf8Bytes =JsonSerializer.SerializeToUtf8Bytes(weatherForecast);
```

### Deserializing to Custom Types
Assume this JSON:
```cs
string jsonString =
    @"{
      ""Date"": ""2019-08-01T00:00:00-07:00"",
      ""TemperatureCelsius"": 25,
      ""Summary"": ""Hot"",
      ""DatesAvailable"": [
          ""2019-08-01T00:00:00-07:00"",
          ""2019-08-02T00:00:00-07:00""
      ],
      ""TemperatureRanges"": {
                      ""Cold"": {
                          ""High"": 20,
          ""Low"": -10
                      },
          ""Hot"": {
                          ""High"": 60,
          ""Low"": 20
          }
      },
      ""SummaryWords"": [
          ""Cool"",
          ""Windy"",
          ""Humid""
      ]
    }
    ";
```

This data can be deserialized as follows:
```cs
WeatherForecast? weatherForecast = 
    JsonSerializer.Deserialize<WeatherForecast>(jsonString);

Console.WriteLine($"Date: {weatherForecast?.Date}");
Console.WriteLine($"TemperatureCelsius: {weatherForecast?.TemperatureCelsius}");
Console.WriteLine($"Summary: {weatherForecast?.Summary}");
```

Output:
```
Date: 8/1/2019 12:00:00 AM -07:00
TemperatureCelsius: 25
Summary: Hot
```

### Deserializing from UTF-8
Assuming the JSON is in a byte array named `jsonUtf8Bytes`:
```cs
var readOnlySpan = new ReadOnlySpan<byte>(jsonUtf8Bytes);
WeatherForecast deserializedWeatherForecast = JsonSerializer.Deserialize<WeatherForecast>(readOnlySpan)!;
```
...or...
```cs
var utf8Reader = new Utf8JsonReader(jsonUtf8Bytes);
WeatherForecast deserializedWeatherForecast = JsonSerializer.Deserialize<WeatherForecast>(ref utf8Reader)!;
```