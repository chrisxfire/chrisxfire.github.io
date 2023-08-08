---
title: overview
date: 2021-11-11T00:00:00-06:00
draft: false
weight: -1
---

# JSON
There are two major .NET libraries for JSON serialization/deserialization:
- Use `System.Text.Json` for performance.  
- Use `Newtonsoft.Json` (aka Json.NET) for a large feature set and developer productivity.  

These notes are for `System.Text.Json`.
- Documentation: https://docs.microsoft.com/en-us/dotnet/api/system.text.json?view=net-6.0

# Security
`System.Text.Json` has a threat model.  See: https://github.com/dotnet/runtime/blob/main/src/libraries/System.Text.Json/docs/ThreatModel.md

# Thread Safety
<r>Warning</r>: JsonDocument is not thread safe.  All other aspects of `System.Text.Json` are thread safe.

# Reflection vs. Source Generation
.NET can gather metadata needed to access properties of objects for serialization/deserialization two ways:
1. Using reflection at run time (default)
2. Using source generation

See notes on [how to enable the source generation method](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/source-generation-modes?pivots=dotnet-7-0).

# Serializing and Deserializing with JsonSerializer
See [notes]({{< ref "jsonserializer">}}).

# Serializing and Deserializing with JSON DOM
Use the DOM when you receive JSON that doesn't have a fixed schema and must be inspected to know what it contains.  
Two JSON DOM approaches:  
1.  `JsonDocument` (see [notes]({{< ref "jsondocument-and-jsonelement" >}}))
    1.  A read-only (immutable) DOM. Cannot be changed after creation. Faster.
    2.  Uses JsonElements.
        1.  `JsonElement` has JSON Array and Object enumerators.
2.  `JsonNode` (see [notes]({{< ref "jsonnode" >}}))
    1.  A mutable DOM. Can be changed after creation. Slower.
    2.  Uses `JsonNode`, `JsonObject`, `JsonArray`, `JsonValue`, and `JsonElement.`

# Deserialize with HttpClient and HttpContent Extension Methods
This technique still requires that you create a response class.
- Documentation: https://docs.microsoft.com/en-us/dotnet/standard/serialization/system-text-json-how-to?pivots=dotnet-6-0#httpclient-and-httpcontent-extension-methods
