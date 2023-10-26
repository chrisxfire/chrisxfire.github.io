---
title: model binding
date: 2023-05-03T00:00:00-06:00
draft: false
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

After each property is bound, [model validation](../model-validation) occurs for that property. The record of what data is bound to the model and any validation errors that occurred are stored in `ControllerBase.ModelState` or `PageModel.ModelState`. 

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

# Data Types for Model Binding
- *Simple type* — a type converted from a single string (using a `TypeConverter` or `TryParse` method).
- *Complex type* — a type converted from multiple input values.

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
public void OnGet( [FromHeader(Name = "Accept-Language")] string language )
```

## `[FromBody]` Attribute
When applied to a complex type parameter, any binding source attributes applied to its properties are ignored:
```cs
public ActionResult<Pet> Create( [FromBody] Pet pet ) // FromBody attribute applied.
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
* <o>Note</o>: This attribute applies only to *posted form* data, not JSON or XML data which is handled by *input formatters*.

## Type Conversion Errors
If a source is found but cannot be converted to the target type, a model state error **is** created (`ModelState.IsValid = false`).

# Binding Simple Types
Model binding can convert source strings into various simple types.

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/mvc/models/model-binding?view=aspnetcore-7.0#simple-types

# Binding Complex Types
To bind, a complex type must have a public default constructor and public writable properties. 

## How Model Binding Matches Properties to Sources
For each property, model binding looks through the sources for `PREFIX.PROPERTY_NAME`. If not found, it looks for `PROPERTY_NAME`.

For query `?Instructor.Id=100&Name=Foo`, and given method `OnGet(Instructor instructor)`, model binding will bind `Id` to `100` and `Name` to `null`. This is because `Instructor.Id` was used for the first query parameter, so it expected `Instructor.Name` (instead of just `Name`) for the second parameter.

## Attributes for Complex Type Targets
<o>Note</o>: these attributes apply to *posted form data* only. They do not apply to *input formatters* which process posted JSON and XML bodies.

### `[Bind]` 
Specifies which properties of a model should be included in model binding.

Can be applied to a class...
```cs
[Bind("LastName,FirstMidName,HireDate")]
public class Instructor
```

...or a method:
```cs
[HttpPost]
public IActionResult OnPost( [Bind("LastName,FirstMidName,HireDate")] Instructor instructor )
```

### `[ModelBinder]`
Specifies the type of model binder used to bind the instance or type.

Can be applied to a parameter...
```cs
[HttpPost]
public IActionResult OnPost( [ModelBinder(typeof(MyInstructorModelBinder))] Instructor instructor )
```

...or property (in this cse, changing the name of the property when it is bound)...
```cs
public class Instructor
{
    [ModelBinder(Name = "instructor_id")]
    public string Id { get; set; }
}
```

...or a type.

### `[BindRequired]`
Causes model binding to add a model state error if binding cannot occur for a property:
```cs
public class InstructorBindRequired
{
    // ...

    [BindRequired]
    public DateTime HireDate { get; set; }
}
```

### `[BindNever]`
Prevents model binding from setting a model's property.  Can be applied to a property or a type.  When applied to a type, excludes all properties of that type from model binding.

## Collections
For collection targets, model binding looks for matches to `PARAMETER_NAME` or `PROPERTY_NAME`.  Avoid using a parameter or property named `index` or `Index` if it is adjacent to a collection value since model binding attempts to use `index` as the index for the collection.

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/mvc/models/model-binding?view=aspnetcore-7.0#collections)

## Dictionaries
For Dictionary targets, model binding looks for matches to `PARAMETER_NAME` or `PROPERTY_NAME`.

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/mvc/models/model-binding?view=aspnetcore-7.0#dictionaries

## Record Types
Model binding and model validation have special considerations with record types:
1. Model binding (and model validation) supports record types with a single constructor:
    ```cs
    public record Person( [Required] string Name, [Range(0, 150)] int Age, [BindNever] int Id );

    public class PersonController
    {
        public IActionResult Index() => View();

        [HttpPost]
        public IActionResult Index(Person person)
        {
            // ...
        }
    }
    ```
2. Binding and validation metadata is used only on parameters and ignored on properties:
    ```cs
    public record Person (string Name, int Age)
    {
        [BindProperty(Name = "SomeName")] // This does not get used
        [Required] // This does not get used
        public string Name { get; init; }
    }
    ```
3. `TryUpdateModel` does not update parameters on a record type:
    ```cs
    public record Person(string Name)
    {
        public int Age { get; set; }
    }

    var person = new Person("initial-name");
    TryUpdateModel(person, ...);
    ```

# Input Formatters (Data in Request Body (JSON & XML))
ASP.NET Core includes a JSON-based input formatter for handling JSON data.

To use the built-in XML input formatters:
1. Add the middleware:  
    `Program.cs`
    ```cs
    builder.Services.AddControllers()
                    .AddXmlSerializerFormatters();
    ```
2. Apply the `Consumes` attribute to controller classes or action methods that expect XML:
    ```cs
    [HttpPost]
    [Consumes("application/xml")]
    public ActionResult<Pet> Create(Pet pet)
    ```

## Configuring Input Formatters
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/mvc/models/model-binding?view=aspnetcore-7.0#customize-model-binding-with-input-formatters

# Excluding Specified Types from Model Binding
To disable model binding on all models of a specified type (ie: `System.Version`):
```cs
builder.Services.AddRazorPages()
    .AddMvcOptions(options =>
    {
        options.ModelMetadataDetailsProviders.Add(new ExcludeBindingMetadataProvider(typeof(Version)));
        options.ModelMetadataDetailsProviders.Add(new SuppressChildValidationMetadataProvider(typeof(Guid)));
    });
```

To disable validation on properties of a specified type (ie: `System.Guid`):
```cs
builder.Services.AddRazorPages()
    .AddMvcOptions(options =>
    {
        options.ModelMetadataDetailsProviders.Add(new ExcludeBindingMetadataProvider(typeof(Version)));
        options.ModelMetadataDetailsProviders.Add(new SuppressChildValidationMetadataProvider(typeof(Guid)));
    });
```

# Invoking Model Binding Manually
<o>Note</o>: this is typically used in Razor Pages and MVC apps to prevent over-posting, or web APIs that consume form data, query strings, and route data.
Use the `TryUpdateModelAsync` method of both the `ControllerBase` and `PageModel` classes. Overloads accept a prefix and value provider:
```cs
if (await TryUpdateModelAsync(newInstructor, "Instructor", x => x.Name, x => x.HireDate!))
{
    _instructorStore.Add(newInstructor);
    return RedirectToPage("./Index");
}

return Page();
```

# Other topics
- [Globalization behavior of model binding route data and query strings](https://learn.microsoft.com/en-us/aspnet/core/mvc/models/model-binding?view=aspnetcore-7.0#globalization-behavior-of-model-binding-route-data-and-query-strings)
- [Special data types](https://learn.microsoft.com/en-us/aspnet/core/mvc/models/model-binding?view=aspnetcore-7.0#special-data-types)