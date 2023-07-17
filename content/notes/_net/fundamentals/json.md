---
title: notes > .net > fundamentals > json
date: 2021-11-11T00:00:00-06:00
draft: false
weight: 1
---

# [JSON](https://docs.microsoft.com/en-us/dotnet/standard/serialization/system-text-json-use-dom-utf8jsonreader-utf8jsonwriter?pivots=dotnet-6-0)
*Serialization*:	Converting types/objects to JSON.
*Deserialization*:	Converting JSON to types/objects.

# Deserializing Using Classes and JsonSerializer.Deserialize
Use when you have a type to deserialize into:  
Given this JSON:
```json
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
Create this model:
```cs
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
```

And deserialize:
```cs
WeatherForecast weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);

public class SomeClass 
{
	// Set this attribute so that even though the JSON field is "name", it will be deserialized into "Name":
	[JsonPropertyName("name")]
	public string Name { get; set; } // Here, name is a JSON field.  Case-sensitive.
}
```
# [Deserialize with JSON DOM](https://docs.microsoft.com/en-us/dotnet/standard/serialization/system-text-json-use-dom-utf8jsonreader-utf8jsonwriter?pivots=dotnet-6-0)

## JsonDocument Technique
The `JsonDocument` technique is immutable and provides faster access to the data.

## JsonNode Technique
The `JsonNode` technique is mutable.

# [Deserialize with HttpClient and HttpContent Extension Methods](https://docs.microsoft.com/en-us/dotnet/standard/serialization/system-text-json-how-to?pivots=dotnet-6-0#httpclient-and-httpcontent-extension-methods)
This technique still requires that you create a response class.

# [JsonSerializerOptions instances](https://docs.microsoft.com/en-us/dotnet/standard/serialization/system-text-json-configure-options?pivots=dotnet-6-0)
