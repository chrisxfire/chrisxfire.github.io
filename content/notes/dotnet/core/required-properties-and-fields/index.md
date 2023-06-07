---
title: notes > dotnet > core > required properties and fields
date: 2022-11-25T00:00:00-06:00
draft: false
---

# Overview
<g>Availability: C# 11 / .NET 7</g>
Properties can be marked `required` to indicate that they must be present in the JSON payload for deserialization to succeed.  Otherwise, `Deserialize` methods throw a `JsonException.`

# Techniques for Marking Fields/Properties
1. Add the `required` modifier to the field/property (C# 11)
2. Annotate the property with `JsonRequiredAttribute` (.NET 7)
    a. Use this technique if the requirement should only apply to deserialization.
3. Modify the `JsonPropertyInfo.IsRequired` property of the contract model (.NET 7)
	
Example
```cs
public class Person 
{
	public required string Name { get; set; }
	public int Age { get; set; }
}
```
or:
```cs
[JsonRequired]
public string Name { get; set; }
```
