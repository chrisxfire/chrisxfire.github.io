---
title: overview
date: 2021-11-11T00:00:00-06:00
draft: false
weight: -1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/overview

There are two major .NET libraries for serializing to, and deserializing from, JSON:
- Use `System.Text.Json` for performance.  
- Use `Newtonsoft.Json` (aka Json.NET) for a large feature set and developer productivity.  

These notes are for `System.Text.Json`. 

There are two approaches for serializing and deserializing with `System.Text.Json`:
1. Using `JsonSerializer`
   * See [notes](./jsonserializer.md).
2. Using the JSON DOM
   * Use the DOM when you receive JSON that doesn't have a fixed schema and must be inspected to know what it contains.  
   * Two JSON DOM approaches:  
     1.  `JsonDocument` (see [notes](jsondocument-and-jsonelement))
        * A read-only (immutable) DOM. Cannot be changed after creation. Faster.
        * Uses `JsonElement`s.
          * `JsonElement` has JSON Array and Object enumerators.
     2.  `JsonNode` (see [notes](jsonnode))
        * A mutable DOM. Can be changed after creation. Slower.
        * Uses `JsonNode`, `JsonObject`, `JsonArray`, `JsonValue`, and `JsonElement.`

## Convenience vs. Control
> Reference: https://devblogs.microsoft.com/dotnet/the-convenience-of-system-text-json/

The APIs in the `System.Text.Json` namespace can be placed on a spectrum of *convenience* vs *control*. 
These APIs are listed from low level (most control) to high level (most convenient):
1. `System.Text.Json.Utf8JsonReader`/`Writer` — for reading and writing JSON documents one node at a time
2. `System.Text.Json.JsonDocument` — for providing a view of the entire JSON document with patterns for reading and writing
3. `System.Text.Json.JsonSerializer` — for automatically serializing and deserializing JSON data

![A horizontal bar chart showing the lines of code required to use each of the above APIs based on a sample app from the reference.
JsonSerializer = 84, NewtonsoftJsonSerializer = 94, JsonNode = 155, Utf8JsonReaderWriter = 668](image.png)

# Security
`System.Text.Json` has a threat model.  See: https://github.com/dotnet/runtime/blob/main/src/libraries/System.Text.Json/docs/ThreatModel.md

# Thread Safety
<r>Warning</r>: `JsonDocument` is not thread safe.  All other aspects of `System.Text.Json` are thread safe.

# Reflection vs. Source Generation
> Documentation: https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/source-generation-modes?pivots=dotnet-7-0

`System.Text.Json` can gather metadata needed to access properties of objects for serialization/deserialization two ways:
1. Using reflection at run time (default)
2. Using source generation

Source generation has two modes: *metadata collection* mode and *serialization optimization* mode:

| Mode                                                | Support for <br /> public properties | Support for <br /> private accessors | Support for <br /> `required` and `init` members |
| --------------------------------------------------- | ------------------------------------ | ------------------------------------ | ------------------------------------------------ |
| Reflection                                          | Yes                                  | Yes                                  | Yes                                              |
| Source generation <br /> Metadata collection        | Yes                                  | Yes                                  | Yes (.NET 8)                                     |
| Source generation <br /> Serialization optimization | Yes                                  | No                                   | No                                               |

## Enabling Source Generation
Follow [instructions here](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/source-generation?pivots=dotnet-7-0) to enable source generation.

# Deserialize with `HttpClient` and `HttpContent` Extension Methods
This technique still requires that you create a response class.
- Documentation: https://docs.microsoft.com/en-us/dotnet/standard/serialization/system-text-json-how-to?pivots=dotnet-6-0#httpclient-and-httpcontent-extension-methods
