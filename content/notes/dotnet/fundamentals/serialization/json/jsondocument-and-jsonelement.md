---
title: notes > .net > fundamentals > serialization > json > jsondocument and jsonelement
date: 2022-01-30T12:11:30-0700
draft: false
weight: 1
---

# Serializing and Deserializing with JsonDocument
## Parsing into a JsonDocument
```cs
JsonDocument doc = JsonDocument.Parse(json); // MUST dispose.
```
Once a `JsonDocument` is disposed, all instances of `JsonElement` are also lost.

## JsonElement
```cs
JsonElement root = doc.RootElement;

JsonElement propertyElement = root.GetProperty("property"); // Get a JsonElement of property.

// Assuming prop is a JSON Array:
foreach (JsonElement prop in propertyElement.EnumerateArray()) 
{
    // Try to get Property from prop and store it in output if succesful:
    if (prop.TryGetProperty("Property", out JsonElement output) 
    {
        value = output;
    }
}
```
## Use JsonDocument to Write JSON
```cs
using FileStream fs = File.Create(outputFile);
using var writer = new Utf8JsonWriter(fs);
using JsonDocument doc = JsonDocument.Parse(json);

JsonElement root = doc.RootElement;

if (root.ValueKind == JsonValueKind.Object) 
{
    writer.WriteStartObject();
}

else { 
    return; 
}

foreach (JsonProperty prop in root.EnumerateObject()) 
{
    prop.WriteTo(writer);
}

writer.WriteEndObject();
writer.Flush(); // Not necessary; writer will auto-flush when disposed.
```
