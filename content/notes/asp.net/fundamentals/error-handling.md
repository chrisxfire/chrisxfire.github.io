---
title: error handling
date: 2023-01-11T00:00:00-07:00
draft: false
weight: 1
---

# [Overview](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/error-handling?view=aspnetcore-7.0)  

ASP.NET Core has built-in error handling features: A developer exception page; custom error pages; static status code pages; startup exception handling.

# developer exception page
Displays detailed information about unhandled request exceptions.  Requires development environment and app built with `WebApplication.CreateBuilder` (not `WebHost.CreateDefaultBuilder`).
- Note:  The developer exception page is not guaranteed to provide any information; use logging.

# Custom exception handler page (for Production environment)
Use `UseExceptionHandler` middleware.
- Catches and logs unhandled exceptions; re-executes request using the original HTTP method in an alternate pipeline with path indicated.
	- To re-execute requests with different methods, create multiple handler methods (Razor Pages) or apply HTTP verb attributes to multiple actions (MVC).
```cs
var app = builder.Build();

if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    app.UseHsts();
}
```

In Razor Pages  
The app templates provides `/Pages/Error.cshtml` and a `PageModel` class (`ErrorModel`).

In MVC apps  
The template provides an `Error` action method and an `Error` view for the `Home` controller.

## accessing the exception
Use `IExceptionHandlerPathFeature`:
```cs
[ResponseCache(Duration = 0, Location = ResponseCacheLocation.None, NoStore = true)]
[IgnoreAntiforgeryToken]
public class ErrorModel : PageModel {
    public string? RequestId { get; set; }
    public bool ShowRequestId => !string.IsNullOrEmpty(RequestId);
    public string? ExceptionMessage { get; set; }

    public void OnGet() {
        RequestId = Activity.Current?.Id ?? HttpContext.TraceIdentifier;

        var exceptionHandlerPathFeature =
            HttpContext.Features.Get<IExceptionHandlerPathFeature>();

        if (exceptionHandlerPathFeature?.Error is FileNotFoundException)
            ExceptionMessage = "The file was not found.";

        if (exceptionHandlerPathFeature?.Path == "/")
        {
            ExceptionMessage ??= string.Empty;
            ExceptionMessage += " Page: Home.";
        }
    }
}
```

# exception handler lambda
Instead of a custom exception handler page, a lambda can be provided to `UseExceptionHandler.`  This allows accessing the error before returning a response:
```cs
var app = builder.Build();

if (!app.Environment.IsDevelopment()) {
    app.UseExceptionHandler(exceptionHandlerApp => {
        exceptionHandlerApp.Run(async context => {
            context.Response.StatusCode = StatusCodes.Status500InternalServerError;

            // using static System.Net.Mime.MediaTypeNames;
            context.Response.ContentType = Text.Plain;

            await context.Response.WriteAsync("An exception was thrown.");

            var exceptionHandlerPathFeature =
                context.Features.Get<IExceptionHandlerPathFeature>();

            if (exceptionHandlerPathFeature?.Error is FileNotFoundException)
                await context.Response.WriteAsync(" The file was not found.");

            if (exceptionHandlerPathFeature?.Path == "/")
                await context.Response.WriteAsync(" Page: Home.");
        });
    });

    app.UseHsts();
}
```

# `UseStatusCodePages`
ASP.NET does not provide a default status code page (like for HTTP/404 errors).  
`UseStatusCodePages` middleware provides ddefault text-only handlers for common error status codes.  
Call `UseStatusCodePages` before request handling middleware.  
`UseStatusCodePage` is not normally used in production.  

```cs
app.UseStatusCodePages();

// or:
// using static System.Net.Mime.MediaTypeNames;
app.UseStatusCodePages(Text.Plain, "Status Code Page: {0}");

// or:
// using static System.Net.Mime.MediaTypeNames;
app.UseStatusCodePages(async statusCodeContext =>
{
    statusCodeContext.HttpContext.Response.ContentType = Text.Plain;

    await statusCodeContext.HttpContext.Response.WriteAsync(
        $"Status Code Page: {statusCodeContext.HttpContext.Response.StatusCode}");
});
```

## `UseStatusCodePagesWithRedirects`
Sends an `HTTP/302 Found` status code and redirects the client to the error handling endpoint provided in the URL template.
The error handling endpoint then (usually) displays error information and returns `HTTP/200`.

```cs
app.UseStatusCodePagesWithRedirects("/StatusCode/{0}"); // {0} is the status code; ~ can be used at start of template for app's PathBase.
```

Remember to create an MVC view or Razor Page for the endpoint.

## `UseStatusCodePagesWithReExecute`
Returns the original status code to the client and generates the response body by re-executing the request pipeline using an alternate path:
```cs
app.UseStatusCodePagesWithReExecute("/StatusCode/{0}");
```

To pass the status code as a query-string parameter:
```cs
app.UseStatusCodePagesWithReExecute("/StatusCode", "?statusCode={0}");
```

# disable status code pages
In an MVC controller or action method, use the `[SkipStatusCodePages]` attribute.  
In a Razor Pages handler method or an MVC controller, use `IStatusCodePagesFeature`:
```cs
public void OnGet()
{
    var statusCodePagesFeature =
        HttpContext.Features.Get<IStatusCodePagesFeature>();

    if (statusCodePagesFeature is not null)
    {
        statusCodePagesFeature.Enabled = false;
    }
}
```

# Exception-handling code & response headers
Remember that, once headers for a response are sent:
- The response's status code cannot be changed
- Any exception pages or handlers cannot run.

The response must be completed or the connection aborted.

# server exception handling
If the underlying HTTP server catches an exception before response headers are sent, it sends `HTTP/500 Internal Server Error` with no body.  
If the server catches an exception after response headers are sent, it closes the connection.

Any request not handled by the app is handled by the server.  

# startup exception handling
This is handled by the host.  See:
- https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/web-host?view=aspnetcore-7.0#capture-startup-errors
- https://learn.microsoft.com/en-us/aspnet/core/fundamentals/host/web-host?view=aspnetcore-7.0#detailed-errors

# problem details
Problem Details are details of errors in an HTTP response.  They are standardized in [RFC 7807](https://www.rfc-editor.org/rfc/rfc7807.html). The problem details service implements `IProblemDetailsService` to create problem details.

To add the problem details service:
```cs
builder.Services.AddProblemDetails();
```

When the problem details service is used, the following middleware generates problem details HTTP responses:
- ExceptionHandlerMiddleware — generates a problem details response when a custom handler is not defined
- StatusCodePageSMiddleware — generates a problem details response by default
- DeveloperExceptionPageMiddleware — generates a problem details response in development when the `Accept` request HTTP header does not include `text/html`.

## customizing problem details
Problem details responses can be customized.

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/error-handling?view=aspnetcore-7.0#customize-problem-details

## producing a problemdetails payload for exceptions
Exceptions can contain Problem Details.

> Documentation: https://learn.microsoft.com/en-us/aspnet/core/fundamentals/error-handling?view=aspnetcore-7.0#produce-a-problemdetails-payload-for-exceptions

# other topics
- [Database error page](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/error-handling?view=aspnetcore-7.0#database-error-page)
- [Exception filters](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/error-handling?view=aspnetcore-7.0#exception-filters)
- [Model state errors](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/error-handling?view=aspnetcore-7.0#model-state-errors)
- [Problem details](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/error-handling?view=aspnetcore-7.0#problem-details)
- [Produce a `ProblemDetails` payload for exceptions](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/error-handling?view=aspnetcore-7.0#produce-a-problemdetails-payload-for-exceptions)
