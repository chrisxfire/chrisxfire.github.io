---
title: notes > .net > fundamentals > serialization > json > jsonnode
date: 2022-01-30T12:35:13-0700
draft: false
weight: 1
---
# [JsonNode](https://docs.microsoft.com/en-us/dotnet/api/system.text.json.nodes.jsonnode?view=net-6.0)
Types: `JsonNode`, `JsonArray`, `JsonObject`, `JsonValue`, `JsonNodeOptions`
```cs
using System.Text.Json.Nodes;

// Create a JsonNode DOM from a JSON string.
JsonNode forecastNode = JsonNode.Parse(jsonString)!; // Parse can also parse a JsonArray or JsonObject

// Write JSON from a JsonNode
var options = new JsonSerializerOptions { WriteIndented = true };
Console.WriteLine(forecastNode!.ToJsonString(options));

// Get value from a JsonNode.
JsonNode temperatureNode = forecastNode!["Temperature"]!;
Console.WriteLine($"Type={temperatureNode.GetType()}"); // Type = System.Text.Json.Nodes.JsonValue`1[System.Text.Json.JsonElement]
Console.WriteLine($"JSON={temperatureNode.ToJsonString()}"); // JSON = 25

// Get a typed value from a JsonNode.
int temperatureInt = (int)forecastNode!["Temperature"]!;
Console.WriteLine($"Value={temperatureInt}"); // Value=25

// Get a JSON object from a JsonNode.
JsonNode temperatureRanges = forecastNode!["TemperatureRanges"]!;
Console.WriteLine($"Type={temperatureRanges.GetType()}"); // Type = System.Text.Json.Nodes.JsonObject
Console.WriteLine($"JSON={temperatureRanges.ToJsonString()}"); // JSON = { "Cold":{ "High":20,"Low":-10},"Hot":{ "High":60,"Low":20} }

// Get a JSON array from a JsonNode.
JsonNode datesAvailable = forecastNode!["DatesAvailable"]!;
Console.WriteLine($"Type={datesAvailable.GetType()}"); // datesAvailable Type = System.Text.Json.Nodes.JsonArray
Console.WriteLine($"JSON={datesAvailable.ToJsonString()}"); // datesAvailable JSON =["2019-08-01T00:00:00", "2019-08-02T00:00:00"]

// Get an array element value from a JsonArray.
JsonNode firstDateAvailable = datesAvailable[0]!;
Console.WriteLine($"Type={firstDateAvailable.GetType()}"); // Type = System.Text.Json.Nodes.JsonValue`1[System.Text.Json.JsonElement]
Console.WriteLine($"JSON={firstDateAvailable.ToJsonString()}"); // JSON = "2019-08-01T00:00:00"

// Get a typed value by chaining references.
int coldHighTemperature = (int)forecastNode["TemperatureRanges"]!["Cold"]!["High"]!;
Console.WriteLine($"TemperatureRanges.Cold.High={coldHighTemperature}"); // TemperatureRanges.Cold.High = 20

// Parse a JSON array
var datesNode = JsonNode.Parse(@"[""2019-08-01T00:00:00"",""2019-08-02T00:00:00""]");
JsonNode firstDate = datesNode![0]!.GetValue<DateTime>();
Console.WriteLine($"firstDate={ firstDate}");  // firstDate = "2019-08-01T00:00:00"
```