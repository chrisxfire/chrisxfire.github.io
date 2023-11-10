---
title: 1. overview (controllers)
date: 2023-08-15T00:00:00-06:00
draft: false
weight: 1
---

# Overview [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/web-api/?view=aspnetcore-7.0)]  

- Controllers are classes that derive from `ControllerBase`.
  - If derived from `Controller`, this would add support for views (for handling web pages rather than API requests).
- Controllers are activated and disposed on a per-request basis.

Knowledge of MVC controllers is needed to use them in controller-based APIs. See [Notes on MVC Controllers](../../../web-apps/mvc/controllers).

# High-Level Process
![A diagram depicting the design of the app. On the left, a box named "Client." On the right, a box labeled "MVC app" with a controller, model, and data access layer. From the client, an arrow to the controller labeled "HTTP request". From the controller, a to/from arrow to the data access layer labeled "read/write". From the controller, an arrow to the client labeled "HTTP response" and a resposne object {Name:"todo1"}. From the model, an arrow to the response object labeled "serialize".](image.png)  

The high-level process for implementing controller-based APIs:
1. VS > File > New > Project > **ASP.NET Core Web API**
   1. **Framework** = **.NET 7.0**
   2. Check **Use controllers**
2. Add a model class
3. Add a database context
4. Register the database context
5. Scaffold a controller
6. Add routing to the controller action methods

# ControllerBase Methods
`CreatedAtAction` is an *action method* in `ControllerBase` that returns a 201 status code.  Other methods:   
| Method                | Description                                      |
| --------------------- | ------------------------------------------------ |
| `BadRequest`          | Returns HTTP 400                                 |
| `ValidationProblem`   | [See notes below](#automatic-http-400-responses) |
| `NotFound`            | Returns HTTP 404                                 |
| `PhysicalFile`        | Returns a file                                   |
| `TryUpdateModelAsync` | Invokes model binding                            |
| `TryValidateModel`    | Invokes model validation                         |

# Attributes
Attributes from the `Microsoft.AspNetCore.Mvc` namespace are used by APIs to configure behavior for controllers and action methods:
```cs
[HttpPost] // Supported HTTP action verb
[ProducesResponseType(StatusCodes.Status201Created)] // HTTP status code that the action method could return
[ProducesResponseType(StatusCodes.Status400BadRequest)] // HTTP status code that the action method could return
public ActionResult<Pet> Create(Pet pet)
{
    pet.Id = _petsInMemoryStore.Any() ? 
                _petsInMemoryStore.Max(p => p.Id) + 1 : 1;
                
    _petsInMemoryStore.Add(pet);
    
    return CreatedAtAction(nameof(GetById), new { id = pet.Id }, pet);
}
```

Common attributes:  
| Attribute         | Description                                                      |
| ----------------- | ---------------------------------------------------------------- |
| `[ApiController]` | See notes below                                                  |
| `[Route]`         | Specifies the URL pattern for a controller or action             |
| `[Bind]`          | Specifies the prefix and properties to include for model binding |
| `[HttpGet]`       | Designates an action that supports HTTP GET requests             |
| `[Consumes]`      | Specifies the data types that an action accepts                  |
| `[Produces]`      | Specifies data types that an action returns                      |

# `ApiController` attribute
`[ApiController]` is applied to a class to specify that it is a *controller* and enables:
- the attribute routing requirement
- automatic HTTP 400 responses
- binding source parameter inference
- multipart/form-data request inference
- problem details for error status codes

This attribute can also be applied to an assembly to define all its controllers as such:  
`Program.cs`
```cs
using Microsoft.AspNetCore.Mvc;

[assembly: ApiController]
var builder = WebApplication.CreateBuilder(args);
// ...
```

## Attribute Routing Requirement
A class that inherits from ControllerBase (a *controller*) and that is decorated with the `[ApiController]` attribute **must** define a route with the `[Route]` attribute:
```cs
[ApiController]
[Route("[controller]")]
public class WeatherForecastController : ControllerBase
```

## Automatic HTTP 400 Responses
The `[ApiController]` attribute makes model validation errors automatically trigger an HTTP 400 response.  So, in such a controller's action method, the following code is not needed:
```cs
if (!ModelState.IsValid)
{
    return BadRequest(ModelState);
}
```

The default response type for an HTTP 400 response is `ValidationProblemDetails`. Instead of calling `BadRequest`, call `ValidationProblem`, which returns a `ValidationProblemDetails` object as well as the automatic response.

### Logging Automatic HTTP 400 Responses
Set `InvalidModelStateResponseFactory` when calling `ConfigureApiBehaviorOptions`:
```cs
var builder = WebApplication.CreateBuilder(args);

builder.Services.AddControllers()
    .ConfigureApiBehaviorOptions(options =>
    {
      // To preserve the default behavior, capture the original delegate to call later.
        var builtInFactory = options.InvalidModelStateResponseFactory;

        options.InvalidModelStateResponseFactory = context =>
        {
            var logger = context.HttpContext.RequestServices
                                .GetRequiredService<ILogger<Program>>();

            // Perform logging here.
            // ...

            // Invoke the default behavior, which produces a ValidationProblemDetails response.
            // To produce a custom response, return a different implementation of IActionResult instead.
            return builtInFactory(context);
        };
    });

var app = builder.Build();

app.UseHttpsRedirection();

app.UseAuthorization();

app.MapControllers();

app.Run();
```

### Disabling Automatic HTTP 400 Responses
Set `SuppressModelStateInvalidFilter` to `true`:
```cs {hl_lines=10}
using Microsoft.AspNetCore.Mvc;

var builder = WebApplication.CreateBuilder(args);

builder.Services.AddControllers()
    .ConfigureApiBehaviorOptions(options =>
    {
        options.SuppressConsumesConstraintForFormFileParameters = true;
        options.SuppressInferBindingSourcesForParameters = true;
        options.SuppressModelStateInvalidFilter = true;
        options.SuppressMapClientErrors = true;
        options.ClientErrorMapping[StatusCodes.Status404NotFound].Link = "https://httpstatuses.com/404";
    });

var app = builder.Build();

app.UseHttpsRedirection();

app.UseAuthorization();

app.MapControllers();

app.Run();
```

# Binding Source Parameter Inference [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/web-api/?view=aspnetcore-7.0#binding-source-parameter-inference)]  

A binding source attribute defines the location at which an action parameter's value is found:

| Attribute        | Binding source                                   |
| ---------------- | ------------------------------------------------ |
| `[FromBody]`     | The HTTP request body                            |
| `[FromForm]`     | HTTP form data in the request body               |
| `[FromHeader]`   | The HTTP request header                          |
| `[FromQuery]`    | The query string portion of the HTTP request     |
| `[FromRoute]`    | The route data of the current request            |
| `[FromServices]` | The HTTP request injected as an action parameter |
| `[AsParameters]` | Method parameters                                |

Without the `[ApiController]` attribute or the binding source attributes above, ASP.NET Core attempts to use the *complex object model binder*. This subsystem pulls data from *value providers* in a defined order.

## Inference Rules
The `[ApiController]` attribute applies these inference rules for the default data sources of action parameters:
- `[FromServices]` — inferred for complex type parameters registered in the DI container.
- `[FromBody]` — inferred for complex type parameters *not* registered in the DI container.
- `[FromForm]` — inferred for action parameters of type `IFormFile` and `IFormFileCollection`; not inferred for any simple or user-defined types.
- `[FromRoute]` — inferred for any action parameter name matching a parameter in the route template.
- `[FromQuery]` — inferred for any other action parameters.

### FromBody Considerations [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/web-api/?view=aspnetcore-7.0#frombody-inference-notes)]  

### FromService Considerations
The parameter binding subsystem binds parameters through dependency injection when the type is configured as a service. Thus, it is not required to explicitly apply the `[FromServices]` attribute to a parameter.

<o>In rare cases, automatic DI can break apps that have a type in DI that is also accepted in an API controller's action  methods</o>. It's not common to have a type in DI and as an argument in an API controller action.  

To disable `[FromServices]` inference globally:
```cs
builder.Services.Configure<ApiBehaviorOptions>(options =>
{
    options.DisableImplicitFromServicesParameters = true;
});
```

## Disabling All Inference Rules
```cs
builder.Services.AddControllers()
    .ConfigureApiBehaviorOptions(options =>
    {
        // ...
        options.SuppressInferBindingSourcesForParameters = true;
        // ...
    });
```

## Multi-part/form Data Request Inference
The `[ApiController]` attribute applies an inference rule for action parameters of type `IFormFile` and `IFormFileCollection`.  The `multipart/form-data` content type is inferred for these types.

To disable:
```cs
builder.Services.AddControllers()
    .ConfigureApiBehaviorOptions(options =>
    {
        // ...
        options.SuppressConsumesConstraintForFormFileParameters = true;
        // ...
```

# Problem Details for Error Status Codes
MVC transforms an error result (HTTP status code 400+) to a result with `ProblemDetails`.

To disable:
```cs
builder.Services.AddControllers()
    .ConfigureApiBehaviorOptions(options =>
    {
        options.SuppressMapClientErrors = true;
        // ...
```

# `[Consumes]` Attribute
By default, actions support all available request content types. The `[Consumes]` attribute constrains this. It can be applied to a controller or an action.

In this example, content type `application/xml` is specified, and any requests that do not specify this content type will receive a 415/Unsupported Media Type response:
```cs
[HttpPost]
[Consumes("application/xml")]
public IActionResult CreateProduct(Product product)
```

This attribute can also resolve ambiguous matches. In this example, POST requests sent to `/api/Consumes` are handled by both of the actions it defines, which is ambiguous. The `[Consumes]` attribute resolves this ambiguity by defining which action method to use based on the `Content-Type` of the request:
```cs
[ApiController]
[Route("api/[controller]")]
public class ConsumesController : ControllerBase
{
    [HttpPost]
    [Consumes("application/json")]
    public IActionResult PostJson(IEnumerable<int> values) =>
        Ok(new { Consumes = "application/json", Values = values });

    [HttpPost]
    [Consumes("application/x-www-form-urlencoded")]
    public IActionResult PostForm([FromForm] IEnumerable<int> values) =>
        Ok(new { Consumes = "application/x-www-form-urlencoded", Values = values });
}
```

# Analyzers [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/web-api/advanced/analyzers?view=aspnetcore-7.0)]  

The MVC analyzers package works with controllers annotated with `ApiControllerAttribute` and builds on [web API conventions](../action-return-types#web-api-conventions). 

Analyzers inspect controller actions and notify you of any that:
- return an undeclared status code
- return an undeclared success result
- document a status code that is not returned
- include an explicit model validation check

## Enabling
`.csproj`
```xml
<PropertyGroup>
    <IncludeOpenAPIAnalyzers>true</IncludeOpenAPIAnalyzers>
</PropertyGroup>
```

# JSON Patch
[JSON Patch](https://datatracker.ietf.org/doc/html/rfc6902) is a standard for applying updates to a resource.  JSON Patch support in ASP.NET Core web API is based on `Newtonsoft.Json` and requires the `Microsoft.AspNetCore.Mvc.NewtonsoftJson` package.

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/web-api/jsonpatch?view=aspnetcore-7.0