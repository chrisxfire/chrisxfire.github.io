---
title: control serialization behavior
date: 2023-07-27T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/dotnet/serialization/json
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/configure-options?pivots=dotnet-7-0)  
JSON serialization/deserialization behavior can be controlled through `JsonSerializerOptions` and various attributes.

# serialization behavior
By default:
- Public properties are serialized
- Fields are ignored
- Casing of JSON names matches the .NET names

# deserialization behavior
By default:
- Property name matching is case sensitive
- Read-only properties are ignored (no value is deserialized into readonly properties)
- Fields are ignored
- Non-public constructors are ignored
- Enums are supported as numbers

# `JsonSerializerOptions` Web Defaults
The defaults in ASP.NET Core apps are different than .NET apps.  See: https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/configure-options#web-defaults-for-jsonserializeroptions

# Guidance for using `JsonSerializerOptions`
> [!CAUTION]
> Do not create a new instance of `JsonSerializerOptions` each time you use it.

If you need a `JsonSerializerOptions` instance that has all default options, use the `JsonSerializerOptions.Default` property.
- Documentation: https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/configure-options?pivots=dotnet-7-0

# overriding default behavior
## properties
| Desired Behavior                             | Approach                                                                                                  | Notes                                                                                                          |
| -------------------------------------------- | --------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------- |
| Use case-insensitive property names          | Use `JsonSerializerOptions.PropertyNameCaseInsensitive = true`                                            | N/A                                                                                                            |
| Customize individual property names          | Use the `[JsonPropertyName("NAME")]` attribute                                                            | N/A                                                                                                            |
| Use camel case property names                | Set `JsonSerializerOptions`'s `PropertyNamingPolicy` property to `JsonNamingPolicy.CamelCase`             | The `[JsonPropertyName]` attribute takes precedence and will override `JsonNamingPolicy`                       |
| Configure the order of serialized properties | Use `[JsonPropertyOrder(N)]` attribute where `N` is an integer specifying order                           | N/A                                                                                                            |
| Ignore individual properties                 | Use the `[JsonIgnore]` attribute on the properties to ignore                                              | This attribute has an optional `Condition` property: `[JsonIgnore(Condition = JsonIgnoreCondition.CONDITION)]` |
| Ignore all read-only properties              | Use `JsonSerializerOptions`'s `IgnoreReadOnlyProperties` property                                         | N/A                                                                                                            |
| Ignore all null-value properties             | Set `JsonSerializerOptions` `DefaultIgnoreCondition` property to `JsonIgnoreCondition.WhenWritingNull`    | N/A                                                                                                            |
| Ignore all default-value properties          | Set `JsonSerializerOptions` `DefaultIgnoreCondition` property to `JsonIgnoreCondition.WhenWritingDefault` | N/A                                                                                                            |

## fields
| Desired Behavior                         | Approach                                             | Notes                                                    |
| ---------------------------------------- | ---------------------------------------------------- | -------------------------------------------------------- |
| Include fields                           | Use the `[JsonInclude]` attribute on the fields      | Alternatively, use `JsonSerializerOptions.IncludeFields` |
| Ignore read-only fields when serializing | Use `JsonSerializerOptions`'s `IgnoreReadOnlyFields` | N/A                                                      |

### marking properties or fields required for json deserialization
> [!IMPORTANT]
> Availability: C# 11

There are three approaches:
1. Via the  `required` modifier    
    ```cs
    using System.Text.Json;

    // The following line throws a JsonException at run time.
    Console.WriteLine(JsonSerializer.Deserialize<Person>("""{"Age": 42}"""));

    public class Person
    {
        public required string Name { get; set; }
        public int Age { get; set; }
    }
    ``````
2. Via the `[JsonRequiredAttribute]`:
    ```cs
    using System.Text.Json;

    // The following line throws a JsonException at run time.
    Console.WriteLine(JsonSerializer.Deserialize<Person>("""{"Age": 42}"""));

    public class Person
    {
        [JsonRequired]
        public string Name { get; set; }
        public int Age { get; set; }
    }
    ```
3. Via the JsonPropertyInfo.IsRequired property of the contract model:
    ```cs
    var options = new JsonSerializerOptions
    {
        TypeInfoResolver = new DefaultJsonTypeInfoResolver
        {
            Modifiers =
            {
                static typeInfo =>
                {
                    if (typeInfo.Kind != JsonTypeInfoKind.Object)
                        return;

                    foreach (JsonPropertyInfo propertyInfo in typeInfo.Properties)
                    {
                        // Strip IsRequired constraint from every property.
                        propertyInfo.IsRequired = false;
                    }
                }
            }
        }
    };
    
    // Deserialization now succeeds even though the Name property isn't in the JSON payload.
    JsonSerializer.Deserialize<Person>("""{"Age": 42}""", options);
    ```

# overriding other behavior
| Desired Behavior                          | Approach                                                                                                                                                 | Notes                         |
| ----------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------- |
| Use camel case dictionary keys            | Set `JsonSerializerOptions`'s `DictionaryKeyPolicy` property to `JsonNamingPolicy.CamelCase`                                                             | Applies to serialization only |
| Use enums as strings                      | Set `JsonSerializerOptions`'s `Converters` property with a `new JsonStringEnumConverter(JsonNamingPolicy.CamelCase)`                                     | N/A                           |
| Allow comments in JSON                    | Set `JsonSerializerOptions`'s `ReadCommentHandling` property to `JsonCommentHandling.Skip`                                                               | N/A                           |
| Allow trailing commas in JSON             | Set `JsonSerializerOptions`'s `AllowTrailingCommas` property to `true`                                                                                   | N/A                           |
| Serialize numbers in quotes               | Set `JsonSerializerOptions`'s `NumberHandling` property to `JsonNumberHandling.AllowReadingFromString`                                                   | N/A                           |
| Deserialize numbers in quotes             | Set `JsonSerializerOptions`'s `NumberHandling` property to `JsonNumberHandling.WriteAsString`                                                            | N/A                           |
| Handle overflow JSON                      | See [this page](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/handle-overflow?pivots=dotnet-7-0#handle-overflow-json) | N/A                           |
| Handle references and circular references | See [this page](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/preserve-references?pivots=dotnet-7-0)                  | N/A                           |
| Deserialize to immutable types            | See [this page](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/immutability?pivots=dotnet-7-0)                         | N/A                           |

## identation options
> [!IMPORTANT]
> Availability: .NET 9

Customize the indentation of written JSON with `JsonSerializerOption`'s `IndentCharacter` and `IndentSize` properties.

# [All built-in naming policies](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/customize-properties#use-a-built-in-naming-policy)
> [!IMPORTANT]
> Availability: .NET 8

As of .NET 8, `JsonNamingPolicy` includes 4 more built-in naming policies:
- `KebabCaseLower`
- `KebabCaseUpper`
- `SnakeCaseLower`
- `SnakeCaseUpper`