---
title: model binding
date: 2023-05-03T00:00:00-06:00
draft: true
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/mvc/models/model-binding?view=aspnetcore-7.0

*Model binding* is the automated process of retrieving data values from an HTTP request and converting the resulting string to a .NET type.

The model binding system:
* Retrieves data from route data, form data, and query strings
* Passes that data to controllers and Razor Pages in method parameters and public properties
* Converts string data to .NET types
* Updates properties of complex types

# Example
Consider this action method...
```cs
[HttpGet("{id}")]
public ActionResult<Pet> GetById(int id, bool dogsOnly)
```

...and this HTTP request:
`https://contoso.com/api/pets/2?DogsOnly=true`

Model binding performs these steps:
1. Get the first parameter of `GetById`, `id`
2. Finds `id="2"` in the route data
3. Converts "2" to 2
4. Gets the next parameter of `GetById`, `dogsOnly`
5. Finds `DogsOnly=true` in the query string (case-insensitive matching)
6. Converts "true" to to `true`

ASP.NET Core then calls `GetById(2, true)`.

After each property is bound, [model validation]({{< ref "./model-validation" >}}) occurs for that property. The record of what data is bound to the model and any validation errors that occurred are stored in `ControllerBase.ModelState` or `PageModel.ModelState`. 

# Model Binding Targets
Model binding has the following *targets*:
- Parameters of the controller action method to which a request is routed
- Parameters of the Razor Pages handler method to which a request is routed
- Public properties of a controller or `PageModel` class if specified by attributes

## `[BindProperty]`
Applied to a public property of a controller or `PageModel` class:
```cs
public class EditModel : PageModel
{
    [BindProperty]
    public Instructor? Instructor { get; set; }
}
```

## `[BindProperties]`
Applied to a controller or `PageModel` class:
```cs
[BindProperties]
public class CreateModel : PageModel
{
    public Instructor? Instructor { get; set; }
}
```

## Model Binding with HTTP GET Requests
By default, <o>properties are not bound</o> for HTTP GET requests. This is because, normally, GET requests only contain a record ID parameter. To force model binding for GET requests:
```cs
[BindProperty(Name = "ai_user", SupportsGet = true)]
public string? ApplicationInsightsCookie { get; set; }
```

# Model Binding Sources
The default sources for HTTP requests are:
1. Form fields
2. Request body (for controllers with the `[ApiController]` attribute)
3. Route data
4. Query string parameters
5. Uploaded files

The source can also be defined explicitly via decorating properties in the model class with these *binding source attributes*:
* `[FromQuery]`
* `[FromRoute]`
* `[FromForm]`
* `[FromBody]`
* `[FromHeader]`

Example:
```cs
public class Instructor
{
    public int Id { get; set; }

    [FromQuery(Name = "Note")]
    public string? NoteFromQueryString { get; set; }
}
```

These attributes have a `Name` property that can be used when the property name does not match the value in the request:
```cs
public void OnGet([FromHeader(Name = "Accept-Language")] string language)
```

## `[FromBody]` Attribute
When applied to a complex type parameter, any binding source attributes applied to its properties are ignored:
```cs
// FromBody attribute applied:
public ActionResult<Pet> Create([FromBody] Pet pet)
```
```cs
public class Pet
{
    public string Name { get; set; } = null!;

    [FromQuery] // Attribute is ignored.
    public string Breed { get; set; } = null!;
}
```

<o>Caution</o>: do not apply `[FromBody]` to more than one parameter per action method; it can only process one parameter.

## Other Sources
Source data is provided to the model binding system by *value providers*. Custom value providers can be built to get data from other sources. See the documentation.

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/mvc/models/model-binding?view=aspnetcore-7.0#additional-sources

# Model State
## Model Properties with No Values Found
By default, if no value is found for a model property, a model state error **is not** created. That property is set to `null` or a default value.

To force a model state error when no value is found for a property, use the `[BindRequired]` attribute.

## Type Conversion Errors
If a source is found but cannot be converted to the target type, a model state error **is** created (`ModelState.IsValid = false`).