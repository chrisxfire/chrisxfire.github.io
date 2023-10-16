---
title: learning path
date: 2023-08-25T00:00:00-06:00
draft: true
weight: 1
---

> Documentation: https://learn.microsoft.com/en-us/dotnet/standard/serialization/

- [ ] Overview
- [ ] JSON serialization...
  - [x] Overview
  - [x] Reflection vs. source generation
  - [x] How to serialize and deserialize JSON
  - [ ] Control serialization behavior...
    - [x] Instantiate JsonSerializerOptions
    - [x] Enable case-insensitive matching
    - [x] Customize property names and values
    - [x] Ignore properties
    - [x] Require properties
    - [x] Allow invalid JSON
    - [x] Handle missing members
    - [x] Handle overflow jSON, use JsonElement or JsonNode
    - [x] Preserve references, handle circular references
    - [x] Deserialize to immutable types, non-public accessors
    - [x] Polymorphic serialization
  - [ ] Read/write JSON without using JsonSerializer...
    - [x] Use DOM
    - [ ] Use Utf8JsonWriter
    - [ ] Use Utf8JsonReader
  - [z] Migrate from Newtonsoft.Json (N/A)
  - [z] Visual Basic support (N/A)
  - [ ] Supported collection types 
  - [ ] Advanced...
- [ ] XML and SOAP serialization...
  - [ ] Overview
  - [ ] XML serialization in depth
  - [ ] Examples
  - [ ] The XML Schema Definition tool
  - [ ] Control XML serialization using attributes
  - [ ] Attributes that control XML serialization
  - [ ] XML serialization with XML Web Services
  - [ ] Attributes that control encoded SOAP serialization
  - [ ] How tos...
  - [ ] XML serialization elements...
  - [ ] Tools...
- [ ] Binary serialization...