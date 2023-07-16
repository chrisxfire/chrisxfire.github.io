---
title: notes > code > .net > libraries > system.text.json > jsonserializer
date: 2021-11-11T10:57:32-0700
draft: false
---
# [JsonSerializer](https://docs.microsoft.com/en-us/dotnet/api/system.text.json.jsonserializer?view=net-6.0)
`Object` –> `JsonSerializer`  

Serialize objects/values to JSON or deserialize JSON to objects/values.  
Supports Async.  

# Resources
[How to serialize and deserialize JSON using C# - .NET | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/standard/serialization/system-text-json-how-to?pivots=dotnet-6-0)

# Attributes
`[JsonInclude]` – include this member in serialization.

# Deserialization Example
```cs
using System.Collections.Generic;
using System.Text.Json;

namespace DeserializeExtra 
{
public class WeatherForecast 
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    public string Summary { get; set; }
    public string SummaryField;
    public IList<DateTimeOffset> DatesAvailable { get; set; }
    public Dictionary<string, HighLowTemps> TemperatureRanges { get; set; }
    public string[] SummaryWords { get; set; }
}

public class HighLowTemps 
{
    public int High { get; set; }
    public int Low { get; set; }
}

public class Program 
{
    public static void Main()

    {
        string jsonString =
        @"
        {
            ""Date"": ""2019-08-01T00:00:00-07:00"",
            ""TemperatureCelsius"": 25,
            ""Summary"": ""Hot"",
            ""DatesAvailable"": [
                ""2019-08-01T00:00:00-07:00"",
                ""2019-08-02T00:00:00-07:00""
            ],
            ""TemperatureRanges"": 
            {
                ""Cold"": 
                {
                    ""High"": 20,
                    ""Low"": -10
                },
                ""Hot"": 
                {
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
        WeatherForecast weatherForecast =
        JsonSerializer.Deserialize<WeatherForecast>(jsonString);

        Console.WriteLine($"Date: {weatherForecast.Date}");
        Console.WriteLine($"TemperatureCelsius: {weatherForecast.TemperatureCelsius}");
        Console.WriteLine($"Summary: {weatherForecast.Summary}");
        }
    }
}
```
output:  
Date: 8/1/2019 12:00:00 AM -07:00  
TemperatureCelsius: 25  
Summary: Hot  
