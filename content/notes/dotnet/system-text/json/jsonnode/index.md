---
title: "notes > dotnet > system text > json > jsonnode"
date: 2022-01-30T12:35:13-0700
draft: false
---
# [JsonNode](https://docs.microsoft.com/en-us/dotnet/api/system.text.json.nodes.jsonnode?view=net-6.0)
```cs
using System.Text.Json.Nodes;
```

Types: `JsonNode`, `JsonArray`, `JsonObject`, `JsonValue`, `JsonNodeOptions`

```cs
// Create a JsonNode DOM from JSON data:
JsonNode node = JsonNode.Parse(json); // Parse can also parse a JSON array or JSON object.

// Print the JSON:
var options = new JsonSerializerOptions { writeIndented = true; }
Console.WriteLine(node.ToJsonString(options); }

// Optionally, get the DOM root:
JsonNode root = node.Root;

// Check to see if a node is a JSON object, array, or value:
node.GetType() // System.Text.Json.Nodes.JsonObject, JsonArray, JsonValue

// Get a JSON object, array, or value (depending on what "Property" is) from a JsonNode:
JsonNode someNode = node["Property"]

// Get a typed value from a JsonNode:
int someInt = (int) node["Property"]

// Get a typed value from a JsonNode with GetValue<T>:
int someInt = node["Property"].GetValue<int>();

// Get a typed value by chaining references:
int someInt = (int) node["Prop1"]!["Prop2"]!["Prop3"];

// Get a subsection of a JSON payload:
JsonObject someSubSection = node["Property"].AsObject();
JsonArray someSubSection2 = node["AnotherProperty"].AsArray();
```