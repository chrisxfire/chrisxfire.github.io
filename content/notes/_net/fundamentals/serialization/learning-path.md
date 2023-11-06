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
  - [ ] How to...
    - [ ] Serialize...
      - [x] How to serialize
      - [ ] Customize property names and values
      - [ ] Ignore properties
      - [ ] Include fields
    - [ ] Deserialize...
      - [ ] How to deserialize
      - [ ] Require JSON properties
      - [ ] Allow invalid JSON
      - [ ] Handle missing members
      - [ ] Handle overflow JSON (using JsonElement or JsonNode)
      - [ ] Deserialize to immutable types
      - [ ] Populate initialized fields
    - [z] Migrate from Newtonsoft.Json
    - [ ] Instantiate JsonSerializerOptions
    - [ ] Enable case-sensitive matching
    - [ ] Handle references
    - [ ] Serialize polymorphic types
    - [ ] Read/write JSON without using JsonSerializer...
      - [x] Use DOM
      - [ ] Use Utf8JsonWriter
      - [ ] Use Utf8JsonReader
  - [ ] Supported collection types
  - [ ] Advanced...
    - [ ] Source generation...
      - [ ] Reflection vs source generation
      - [ ] Source-generation modes
      - [ ] Use source generation
    - [ ] Customize character encoding
    - [ ] Write custom converters
    - [ ] Customize contracts
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