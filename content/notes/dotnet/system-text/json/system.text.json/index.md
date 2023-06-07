---
title: "notes > dotnet > system text > json > system.text.json"
date: 2021-11-11T10:55:56-0700
draft: true
---
# [System.Text.Json](https://docs.microsoft.com/en-us/dotnet/api/system.text.json?view=net-6.0)
Use System.Text.Json for performance.
Use Newtonsoft.Json (aka Json.NET) for a large feature set and developer productivity.

Use the DOM when you receive JSON that doesn't have a fixed schema and must be inspected to know what it contains.
Two JSON DOM options:
1.  `JsonDocument`
    1.  A read-only (immutable) DOM. Cannot be changed after creation. Faster.
    2.  Uses `JsonElement`s.
        1.  JsonElement has JSON Array and Object enumerators.
2.  `JsonNode`
    1.  A mutable DOM. Can be changed after creation. Slower.
    2.  Uses `JsonNode`, `JsonObject`, `JsonArray`, `JsonValue`, and `JsonElement`.

# Customizing Individual Property Names
Use the [JsonPropertyName] attribute.
Given this JSON:
`{`
`"Wind": 35`
`}`

The Wind object can be serialized into a property of a different name:
[JsonPropertyName("Wind")]
public int WindSpeed { get; set; }

# Customizing Casing of All Property Names
Use a `PropertyNamingPolicy JsonSerializerOption`:
var serializeOptions = new JsonSerializerOptions
{
PropertyNamingPolicy = JsonNamingPolicy.CamelCase,
WriteIndented = true
};
jsonString = JsonSerializer.Serialize(weatherForecast, serializeOptions);

Given this JSON:
`{`
`"date": "2019-08-01T00:00:00-07:00",`
`"temperatureCelsius": 25,`
`"summary": "Hot",`
`"Wind": 35`
`}`

Now, this class will deserialize the JSON:
public class WeatherForecast
{
public DateTimeOffset Date { get; set; }
public int TemperatureCelsius { get; set; }
public string? Summary { get; set; }
[JsonPropertyName("Wind")]
public int WindSpeed { get; set; }
}

# Customizing Property Names for Dictionary Keys
Applies to serialization only.
Use a `DictionaryKeyPolicy JsonSerializerOption`:
var options = new JsonSerializerOptions
{
DictionaryKeyPolicy = JsonNamingPolicy.CamelCase,
WriteIndented = true
};
jsonString = JsonSerializer.Serialize(weatherForecast, options);

# Ignoring Individual Properties
Use the `[JsonIgnore]` attribute:
public class WeatherForecastWithIgnoreAttribute
{
public DateTimeOffset Date { get; set; }
public int TemperatureCelsius { get; set; }
[JsonIgnore]
public string? Summary { get; set; }
}

`JSON:`
`{`
`"Date": "2019-08-01T00:00:00-07:00",`
`"TemperatureCelsius": 25,`
`}`

# Ignoring All Read-Only Properties
A read-only property has a public getter, but not a public setter.
Use the `IgnoreReadOnlyProperties JsonSerializerOption`:
var options = new JsonSerializerOptions
{
IgnoreReadOnlyProperties = true,
WriteIndented = true
};
jsonString = JsonSerializer.Serialize(weatherForecast, options);

# Handling Overflow (JSON payload does not match target type)
Assume this target type:
public class WeatherForecast
{
public DateTimeOffset Date { get; set; }
public int TemperatureCelsius { get; set; }
public string? Summary { get; set; }
}

Assume this JSON payload:
`{`
`"Date": "2019-08-01T00:00:00-07:00",`
`"TemperatureCelsius": 25,`
`"Summary": "Hot",`
`"DatesAvailable": [`
`"2019-08-01T00:00:00-07:00",`
`"2019-08-02T00:00:00-07:00"`
`],`
`"SummaryWords": [`
`"Cool",`
`"Windy",`
`"Humid"`
`]`
`}`

Deserializing that JSON payload into the `WeatherForecast` type results in `DatesAvailable` and `SummaryWords` being lost. To capture such extra data, add a Dictionary with a `JsonExtensionData` attribute:
public class WeatherForecastWithExtensionData
{
public DateTimeOffset Date { get; set; }
public int TemperatureCelsius { get; set; }
public string? Summary { get; set; }
[JsonExtensionData]
public Dictionary<string, JsonElement>? ExtensionData { get; set; }
}

Now, the `DatesAvailable` and `SummaryWords` arrays in the JSON payload will be captured in the `ExtensionData` dictionary.