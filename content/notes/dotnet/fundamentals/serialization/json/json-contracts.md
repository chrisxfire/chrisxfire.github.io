---
title: notes > .net > fundamentals > serialization > json > json contracts
date: 2023-07-30T00:00:00-06:00
draft: false
weight: 1
---

# Overview
- `System.Text.Json` creates a JSON *contract* for each .NET type that determines how it is serialized and deserialized.  
- The contract is created based on the shape of the type — its properties, fields and interfaces it implements.
- Types are mapped to contracts either at run time (via reflection) or compile time (via source generation).
- Documentation: https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/custom-contracts

# Customizing JSON Contracts
<g>Availability: .NET 7</g> 


## Modifiers
A modifier is an `Action<JsonTypeInfo>` or a `static void` method with a `JsonTypeInfo` parameter that gets the current state of the contract as an argument and makes modifications to it.
- Modify the `JsonTypeInfo.Get` property to change serialization behavior
- Modify the `JsonTypeInfo.Set` property to change deserialization behavior
- Create a new property using `JsonTypeInfo.CreateJsonPropertyInfo(Type, String)` and add it to the `JsonTypeInfo.Properties` collection

### Modifications
The following modificatinos can be made:  
| Modification                                  | Applicable to this JsonTypeInfo.Kind | How                                                                 |
| --------------------------------------------- | ------------------------------------ | ------------------------------------------------------------------- |
| Customize a property's value                  | `JsonTypeInfoKind.Object`            | Modify the `Get` or `Set` delegate of the `JsonPropertyInfo` object |
| Add or remove properties                      | `JsonTypeInfoKind.Object`            | Add or remove items from `JsonTypeInfo.Properties` list             |
| Conditionally serialize a property            | `JsonTypeInfoKind.Object`            | Modify the `JsonPropertyInfo.ShouldSerialize` predicate             |
| Customize number handling for a specific type | `JsonTypeInfoKind.None`              | Modify the `JsonTypeInfo.NumberHandling` value                      |

## Process
To customize JSON contracts:
1. Create modifiers
2. Create a `JsonSerializerOptions` instance
3. In `JsonSerializerOptions`'s `TypeInfoResolver` property, set a new `DefaultJsonTypeInfoResolver` instance
4. In `TypeInfoResolver`'s `Modifiers` property, assign custom actions

Example:
```cs
JsonSerializerOptions options = new()
{
    TypeInfoResolver = new DefaultJsonTypeInfoResolver
    {
        Modifiers =
        {
            MyCustomModifier1,
            MyCustomModifier2
        }
    }
};
```