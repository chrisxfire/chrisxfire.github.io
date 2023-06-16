---
title: notes > .net > namespaces > system.text.json > jsonserializeroptions
date: 2021-12-23T16:21:39-0700
draft: false
---
# [JsonSerializerOptions](https://docs.microsoft.com/en-us/dotnet/api/system.text.json.jsonserializeroptions?view=net-6.0)

# Configuring Options
```cs
var options = new JsonSerializerOptions() { Property = value };
// or
JsonSerializerptions options = new() { Property = value };
```

# Calling Deserialize() with Options
```cs
JsonSerializer.Deserialize(content, options)
```

## `PropertyNameCaseInsensitive`
Setting this to true allows for properties to have different casing than the incoming JSON object.  

Given the following JSON:
```json
{
    "date": "2019-08-01T00:00:00-07:00",
    "temperatureCelsius": 25,
    "summary": "Hot",
}
```

This class can be used to deserialize:
```cs
public class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    public string? Summary { get; set; }
}
```
