---
title: notes > .net > fundamentals > serialization > json > overview
date: 2021-11-11T00:00:00-06:00
draft: false
weight: -1
---

# JSON
- *Serialization*:	Converting types/objects to JSON.
- *Deserialization*:	Converting JSON to types/objects.
- Use [`System.Text.Json`](https://docs.microsoft.com/en-us/dotnet/api/system.text.json?view=net-6.0) for performance.  
- Use `Newtonsoft.Json` (aka Json.NET) for a large feature set and developer productivity.  

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

# Deserialize with JSON DOM
Use the DOM when you receive JSON that doesn't have a fixed schema and must be inspected to know what it contains.  
Two JSON DOM options:  
1.  `JsonDocument`
    1.  A read-only (immutable) DOM. Cannot be changed after creation. Faster.
    2.  Uses JsonElements.
        1.  `JsonElement` has JSON Array and Object enumerators.
2.  `JsonNode`
    1.  A mutable DOM. Can be changed after creation. Slower.
    2.  Uses `JsonNode`, `JsonObject`, `JsonArray`, `JsonValue`, and `JsonElement.`
* Documentation: https://docs.microsoft.com/en-us/dotnet/standard/serialization/system-text-json-use-dom-utf8jsonreader-utf8jsonwriter?pivots=dotnet-6-0

# Customizing Individual Property Names
Use the `[JsonPropertyName]` attribute.  
Given this JSON:
```json
{
    "Wind": 35
}
```

The `Wind` object can be serialized into a property of a different name:
```cs
[JsonPropertyName("Wind")]
public int WindSpeed { get; set; }
```

# Customizing Casing of All Property Names
Use a `PropertyNamingPolicy` `JsonSerializerOption`:
```cs
var serializeOptions = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase,
    WriteIndented = true
};

jsonString = JsonSerializer.Serialize(weatherForecast, serializeOptions);
```
Given this JSON:
```json
{
    "date": "2019-08-01T00:00:00-07:00",
    "temperatureCelsius": 25,
    "summary": "Hot",
    "Wind": 35
}
```

Now, this class will deserialize the JSON:
```cs
public class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    public string? Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

# Customizing Property Names for Dictionary Keys
Applies to serialization only.  
Use a `DictionaryKeyPolicy` `JsonSerializerOption`:
```cs
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase,
    WriteIndented = true
};

jsonString = JsonSerializer.Serialize(weatherForecast, options);
```

# Ignoring Individual Properties
Use the `[JsonIgnore]` attribute:
```cs
public class WeatherForecastWithIgnoreAttribute
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    [JsonIgnore]
    public string? Summary { get; set; }
}
```
JSON:
```json
{
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
}
```

# Ignoring All Read-Only Properties
A read-only property has a public getter, but not a public setter.  
Use the `IgnoreReadOnlyProperties` `JsonSerializerOption`:  
```cs
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true,
    WriteIndented = true
};

jsonString = JsonSerializer.Serialize(weatherForecast, options);
```

# Handling Overflow (JSON payload does not match target type)
Assume this target type:
```cs
public class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    public string? Summary { get; set; }
}
```

Assume this JSON payload:
```json
{
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot",
    "DatesAvailable": [
        "2019-08-01T00:00:00-07:00",
        "2019-08-02T00:00:00-07:00"
    ],
    "SummaryWords": [
        "Cool",
        "Windy",
        "Humid"
    ]
}
```

Deserializing that JSON payload into the `WeatherForecast` type results in `DatesAvailable` and `SummaryWords` being lost. To capture such extra data, add a Dictionary with a `JsonExtensionData` attribute:
```cs
public class WeatherForecastWithExtensionData
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    public string? Summary { get; set; }
    [JsonExtensionData]
    public Dictionary<string, JsonElement>? ExtensionData { get; set; }
}
```

Now, the `DatesAvailable` and `SummaryWords` arrays in the JSON payload will be captured in the `ExtensionData` dictionary.

# Deserialize with HttpClient and HttpContent Extension Methods
This technique still requires that you create a response class.
- Documentation: https://docs.microsoft.com/en-us/dotnet/standard/serialization/system-text-json-how-to?pivots=dotnet-6-0#httpclient-and-httpcontent-extension-methods

# [JsonSerializerOptions instances](https://docs.microsoft.com/en-us/dotnet/standard/serialization/system-text-json-configure-options?pivots=dotnet-6-0)

