---
title: "http logging"
date: 2023-05-14T00:00:00-06:00
draft: false
weight: 1
---

# Overview
HTTP logging middleware logs information about incoming HTTP requests and HTTP responses including common properties, headers, and the body.

<o>Caution</o>: HTTP logging can reduce the performance of an app, especially when logging request/response bodies.  
<r>Warning</r>: HTTP logging can potentially log personally identifiable information.

# Enabling
1. Call `AddHttpLogging` and `UseHttpLogging`:  
    `Program.cs`  
    ```cs {hl_lines=[3,7]}
    var builder = WebApplication.CreateBuilder(args);

    // the empty lambda here uses default logging options:
    builder.Services.AddHttpLogging(o => { });

    var app = builder.Build();

    app.UseHttpLogging();

    if (!app.Environment.IsDevelopment())
        app.UseExceptionHandler("/Error");

    app.UseStaticFiles();

    app.MapGet("/", () => "Hello World!");

    app.Run();
    ```
3. Update `appsettings.Development.json` at the `"LogLevel"` statement:
    ```json
    "Microsoft.AspNetCore.HttpLogging.HttpLoggingMiddleware": "Information"
    ```

# Configuration
## Order of Precedence
Logging configuration follows this order of precedence:
1. Global configuration from `HttpLoggingOptions` (set by calling `AddHttpLogging)`
2. Endpoint-specific configuration (via `WithHttpLogging` extension method (Minimal API apps) or `[HttpLogging]` attribute (Controller-based apps))
3. `IHttpLoggingInterceptor`
 
## Overview
Use the lambda in `AddHttpLogging` to configure `HttpLoggingOptions`:
```cs
// ...
builder.Services.AddHttpLogging(logging =>
{
    logging.LoggingFields = HttpLoggingFields.All;
    logging.RequestHeaders.Add("sec-ch-ua");
    logging.ResponseHeaders.Add("MyResponseHeader");
    logging.MediaTypeOptions.AddText("application/javascript");
    logging.RequestBodyLogLimit = 4096;
    logging.ResponseBodyLogLimit = 4096;
    logging.CombineLogs = true;
});
// ...
```

<o>Note</o>: to enable static file HTTP logging, call `UseHttpLogging` *before* the call to `UseStaticFiles`. 

## Details on `HttpLoggingOptions`
From the above example:
- `HttpLoggingOptions.LoggingFields` — an enum that configures specific parts of the request and response to log
- `HttpLoggingOptions.RequestHeaders` and `ResponseHeaders` — collections of header names to log. In the above example, `sec-ch-ua` request headers are logged.
- `HttpLoggingOptions.MediaTypeOptions` — provides configuration for selecting which encoding to use for a specific media type.
  - This approach can also be used to log, for example, form data (which is not normally logged), but specifying a media type such as `application/x-www-form-urlencoded` or `multipart/form-data`.
  - `MediaTypeOptions` includes methods `AddText`, `AddBinary`, and `Clear`.
- `HttpLoggingOptions.RequestBodyLogLimit` and `ResponseBodyLogLimit` — set the limit, in bytes, to which to limit the logging of a request or response body.
- `HttpLoggingOptions.CombineLogs` — boolean if all logs for a request and response should be consolidated into one log at the end.

## Endpoint Logging Configuration
### In Minimal API Apps
Use `WithHttpLogging` extension method:
```cs
app.MapGet("/response", () => "Hello World! (logging response)")
    .WithHttpLogging(HttpLoggingFields.ResponsePropertiesAndHeaders);
```

### In Controller-based Apps
Use `[HttpLogging]` attribute:
```cs
app.MapGet("/duration", [HttpLogging(loggingFields: HttpLoggingFields.Duration)]
    () => "Hello World! (logging duration)");
```

# IHttpLoggingInterceptor [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/http-logging/?view=aspnetcore-8.0&preserve-view=true#ihttplogginginterceptor)]
An interface for a service that can be implemented to handle per-request and per-response callbacks for customizing what details get logged.