---
title: 4. error handling
date: 2023-08-15T00:00:00-06:00
draft: false
weight: 4
---

# Overview [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/web-api/handle-errors?view=aspnetcore-7.0)]  

[Notes on Error Handling in ASP.NET Core](../../../fundamentals/error-handling) apply.

# Exception Handling
In non-development environments:
1. Call `UseExceptionHandler` to add exception handling middleware:  
    `Program.cs`
    ```cs
    var app = builder.Build();

    app.UseHttpsRedirection();

    if (!app.Environment.IsDevelopment())
        app.UseExceptionHandler("/error");

    app.UseAuthorization();

    app.MapControllers();

    app.Run();
    ```
2. Configure a controller action to respond to the `/error` route:
    `SomeController.cs`
    ```cs
    [Route("/error")]
    // If using OpenAPI, mark this action with [ApiExplorerSettings(IgnoreApi = true)] to exclude this
    // error handler action from the app's OpenAPI specification:
    public IActionResult HandleError() => Problem();
    ```

If using exception handling middleware in both development and non-development environments:  
1. Register exception handling middleware for both environments:
    `Program.cs`
    ```cs
    if (app.Environment.IsDevelopment())
        app.UseExceptionHandler("/error-development");
    
    else
        app.UseExceptionHandler("/error");
    ```
2. Configure controllers for both routes:  
    `SomeController.cs`
    ```cs
    [Route("/error-development")]
    public IActionResult HandleErrorDevelopment([FromServices] IHostEnvironment hostEnvironment)
    {
        if (!hostEnvironment.IsDevelopment())
            return NotFound();

        var exceptionHandlerFeature =
            HttpContext.Features.Get<IExceptionHandlerFeature>()!;

        return Problem(
            detail: exceptionHandlerFeature.Error.StackTrace,
            title: exceptionHandlerFeature.Error.Message);
    }

    [Route("/error")]
    public IActionResult HandleError() => Problem();
    ```

# Use Exceptions to Modify the Response
The contents of the response can be modified outside of the controller.
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/web-api/handle-errors?view=aspnetcore-7.0#use-exceptions-to-modify-the-response

# Validation Failure Error Response
The error response from a validation failure can also be customized.
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/web-api/handle-errors?view=aspnetcore-7.0#validation-failure-error-response

# Client Error Response
Error results (HTTP/400+) are transformed into a `ProblemDetails` by MVC in web APIs. Its body looks like this:
```json
{
  "type": "https://tools.ietf.org/html/rfc7231#section-6.5.1",
  "title": "Bad Request",
  "status": 400,
  "traceId": "00-84c1fd4063c38d9f3900d06e56542d48-85d1d4-00"
}
```

Automatic creation of `ProblemDetails` for error results is enabled by default.  It can be disabled:  
`Program.cs`
```cs
builder.Services.AddControllers()
    .ConfigureApiBehaviorOptions(options =>
    {
        options.SuppressMapClientErrors = true;
    });
```

And can be configured via `IProblemDetailsService`, `ProblemDetailsFactory`, or `ApiBehaviorOptions`:

## `IProblemDetailsService`
See [notes on Problem Details](../../../fundamentals/error-handling#problem-details).

## `ProblemDetailsFactory`
To customize the problem details response with `ProblemDetailsFactory`, register a custom implementation:  
`Program.cs`
```cs
builder.Services.AddControllers();
builder.Services.AddTransient<ProblemDetailsFactory, SampleProblemDetailsFactory>();
```

## `ApiBehaviorOptions`
To customize the problem details response with `ApiBehaviorOptions`, use its `ClientErrorMapping` property:
```cs
builder.Services.AddControllers()
    .ConfigureApiBehaviorOptions(options =>
    {
        // change the Link property for 404 responses:
        options.ClientErrorMapping[StatusCodes.Status404NotFound].Link =
            "https://httpstatuses.com/404";
    });
```