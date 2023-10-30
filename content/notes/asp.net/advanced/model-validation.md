---
title: model validation
date: 2023-08-27T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/mvc/models/validation?view=aspnetcore-7.0

- *Model state* represents errors that come from either the *model binding* or *model validation* subsystems. 
- Model validation occurs after model binding and reports errors where the data does not conform to business rules (like a 0 in a field that expects a value from 1 to 5).
- Both model binding and model validation occur before a controller action method, or a Razor Pages handler method, executes.
- When a validation error occurs, model validation generates a `ModelStateDictionary` with the property name as the error key.
- For web apps, <o>the app must inspect `ModelState.IsValid`</o> and react appropriately. 

Example for MVC app (controllers and views):
```cs {hl_lines=[3,4]}
public async Task<IActionResult> Create(Movie movie)
{
    if (!ModelState.IsValid)
        return View(movie);

    _context.Movies.Add(movie);
    await _context.SaveChangesAsync();

    return RedirectToAction(nameof(Index));
}
```

Note: Web API controllers do not need to check `ModelState.IsValid` if they are decorated with `[ApiController]` — assuming [automatic HTTP 400](../../api/controller-based-apis/overview#automatic-http-400-responses) responses are enabled (default).


# Repeating Validation
Although validation is automatic, it can be re-run if needed by calling `ModelStateDictionary.ClearValidationState` and then `TryValidateModel`:
```cs {hl_lines=[6,7]}
public async Task<IActionResult> OnPostTryValidateAsync()
{
    var modifiedReleaseDate = DateTime.Now.Date;
    Movie.ReleaseDate = modifiedReleaseDate;

    ModelState.ClearValidationState(nameof(Movie));
    if (!TryValidateModel(Movie, nameof(Movie)))
        return Page();

    _context.Movies.Add(Movie);
    await _context.SaveChangesAsync();

    return RedirectToPage("./Index");
}
```

# Validation Attributes
Use to define validation rules for model properties:
```cs
public class Movie
{
    // ...
    
    [ClassicMovie(1960)]
    [DataType(DataType.Date)]
    [Display(Name = "Release Date")]
    public DateTime ReleaseDate { get; set; }

    [Required]
    [StringLength(1000)]
    public string Description { get; set; } = null!;

    [Range(0, 999.99)]
    public decimal Price { get; set; }
    
    // ...
}
```

See also: [System.ComponentModel.DataValidation](https://learn.microsoft.com/en-us/dotnet/api/system.componentmodel.dataannotations?view=net-7.0)

## Error Messages
Validation attributes allow for defining the error message that is displayed on invalid input:
```cs
// {0} is the property name; {2} is MinimumLength and {1} is StringLength:
[StringLength(8, ErrorMessage = "{0} length must be between {2} and {1}.", MinimumLength = 6)]
```

## Use JSON Property Names in Validation Errors
Configure like this. Note that the JsonNamingPolicy is optional:
```cs {hl_lines=[7,8]}
using Microsoft.AspNetCore.Mvc.ModelBinding.Metadata;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddControllers(options =>
{
    options.ModelMetadataDetailsProviders.Add(
        new SystemTextJsonValidationMetadataProvider(JsonNamingPolicy.CamelCase));
});
// ...
```

## `[Required]` Attribute and Non-nullable Reference Types
MVC validates non-nullable properties or parameters as if they had been decorated with `[Required(AllowEmptyStrings = false)]`.  

For example, consider this model:
```cs
public class Person
{
    public string Name { get; set; }
}
```

A missing value for `Name` yields a validation error.

To disable this behavior:
```cs
builder.Services.AddControllers(
    options => options.SuppressImplicitRequiredAttributeForNonNullableReferenceTypes = true);
```

### `[Required]` Validation on the Server
On the server, a required value is considered missing if the property is null. <o>A non-nullable field is always valid</o>—the `[Required]` attribute's error message is <o>never</o> displayed.

However, <o>a non-nullable</o> field may fail model validation with an error message such as `The value '' is invalid`. To customize this message, either make the field nullable, or:
```cs {hl_lines=[5]}
builder.Services.AddRazorPages()
    .AddMvcOptions(options =>
    {
        options.MaxModelValidationErrors = 50;
        options.ModelBindingMessageProvider.SetValueMustNotBeNullAccessor(_ => "The field is required.");
    });

builder.Services.AddSingleton
    <IValidationAttributeAdapterProvider, CustomValidationAttributeAdapterProvider>();
```

### `[Required]` Validation on the Client
On the client:
1. A value is considered present only if input is entered (including whitespace).
2. Validation handles non-nullable types the same as nullables. 

So, you get client-side validation even without the `[Required]` attribute.

## `[Remote]` Attribute
Implements client-side validation that requires calling a method on the server to determine whether field input is valid.

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/mvc/models/validation?view=aspnetcore-7.0#remote-attribute

## Custom Attributes
Use custom attributes in scenarios where built-in attributes are insufficient.

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/mvc/models/validation?view=aspnetcore-7.0#custom-attributes

# Top-Level Node Validation
Model-bound top-level nodes (action parameters; controller properties; page handler parameters; page model properties) are validated in addition to model properties.

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/mvc/models/validation?view=aspnetcore-7.0#top-level-node-validation

# Maximum Errors, Maximum Recursion
Validation stops after the maximum number of validation errors is reached (default=200).  To configure:
```cs
builder.Services.AddRazorPages()
    .AddMvcOptions(options =>
    {
        options.MaxModelValidationErrors = 50;
    });

// ...
```

For models that are deep or infinitely recursive, validation may result in a stack overflow. The validation depth (default=32) can be configured:
```cs
builder.Services.AddRazorPages()
    .AddMvcOptions(options =>
    {
        options.MaxValidationDepth(128);
    });

// ...
```

# Client-side Validation
Prevents submission until the form is valid. There is a jQuery Unobtrusive Validation script that is a custom Microsoft library built on the jQuery Validation plug-in. Prevents having to code validation logic both server side and client side. 

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/mvc/models/validation?view=aspnetcore-7.0#client-side-validation

# Problem Details
See [notes on Problem Details](../../fundamentals/error-handling#problem-details)