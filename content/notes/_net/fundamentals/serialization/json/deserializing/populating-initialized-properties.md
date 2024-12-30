---
title: populating initialized properties
date: 2024-12-13T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/dotnet/serialization/json/deserializing
---

# [Overview](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/populate-properties)
> [!IMPORTANT]
> Availability: .NET 8

When deserializing JSON, you can either replace or populate .NET properties and fields.

# setting the behavior
This is done by setting the `JsonObjectCreationHandling` attribute to `JsonObjectCreationHandling.Populate`. This attribute can be set to one
setting at the type level and another setting at the property level to override the behavior inherited from the type:
```cs
// Type-level preference is Populate.
[JsonObjectCreationHandling(JsonObjectCreationHandling.Populate)]
class B
{
    // For this property only, use Replace behavior.
    [JsonObjectCreationHandling(JsonObjectCreationHandling.Replace)]
    public List<int> Numbers1 { get; } = [1, 2, 3];
    public List<int> Numbers2 { get; set; } = [1, 2, 3];
}
```

The setting can also be applied globally by setting `JsonSerializerOptions.PreferredObjectCreationHandling`:
```cs
var options = new JsonSerializerOptions
{
    PreferredObjectCreationHandling = JsonObjectCreationHandling.Populate
};
```

# Replace (default) behavior
Consider this code:
```cs
class A
{
    public List<int> Numbers1 { get; } = [1, 2, 3];
    public List<int> Numbers2 { get; set; } = [1, 2, 3];
}

A? a = JsonSerializer.Deserialize<A>("""{"Numbers1": [4,5,6], "Numbers2": [4,5,6]}""");
```

After the above JSON is deserialized onto `A`:
- `Numbers1` will still have values 1, 2, 3 (it's a read-only property).
- `Numbers2` will have a new list allocated and the values from the JSON added. Its values will be 4, 5, 6.

# populate behavior
This behavior modifies (*populates*) properties and fields instead of replacing them. This is also true for read-only properties.

For a property that is an object with properties, the object is reused without clearing. Its mutable properties are updated to the JSON values.

## Example: collection type properties
For collection type properties, the object is reused without clearing. Any prepopulated elements in the collection will remain:
```cs
[JsonObjectCreationHandling(JsonObjectCreationHandling.Populate)]
class A
{
    public List<int> Numbers1 { get; } = [1, 2, 3];
    public List<int> Numbers2 { get; set; } = [1, 2, 3];
}

A? a = JsonSerializer.Deserialize<A>("""{"Numbers1": [4,5,6], "Numbers2": [4,5,6]}""");
```

After the above JSON is deserialized onto `A`: `Numbers1` and `Numbers2` will have values 1, 2, 3, 4, 5, 6.

## Example: Struct properties
For a struct type property, the object is not reused (since it's a value type). 
For its mutable properties, any existing values are kept and new values from the JSON are added:

```cs
C? c = JsonSerializer.Deserialize<C>("""{"S1": {"Value2": 5}}""");

class C
{
    public C()
    {
        _s1 = new S
        {
            Value1 = 10
        };
    }

    private S _s1;

    [JsonObjectCreationHandling(JsonObjectCreationHandling.Populate)]
    public S S1
    {
        get { return _s1; }
        set { _s1 = value; }
    }
}

struct S
{
    public int Value1 { get; set; }
    public int Value2 { get; set; }
}
```