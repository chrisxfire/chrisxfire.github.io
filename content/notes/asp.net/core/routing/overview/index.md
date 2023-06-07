---
title: notes > asp.net > core > routing > overview
date: 2023-01-09T00:00:00-06:00
draft: false
---

# Overview
Routing is matching incoming HTTP requests and dispatching them to the app's executable endpoints.  
Endpoints are the app's units of executable request-handling code.

Routing can be configured via controllers, Razor Pages, SignalR, gRPC services, middleware, and delegates & lambdas registered with routing.

## Endpoints
Endpoints handle requests and execute code to generate a response.  They are defined in `Program.cs`.

## Basic Routing Example
```cs
var builder = WebApplication.CreateBuilder(args);
var app = builder.Build();

// This is an endpoint:
app.MapGet("/", () => "Hello World!"); // When a request is sent to /, "Hello World" is written to the response

app.Run();
```

If the request is not a GET request or the root of the URL is not /, no route is matched and an HTTP/404 is returned.

[More Topics…](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/routing?view=aspnetcore-7.0)
- URL generation reference
    - Troubleshooting URL generation with logging
    - Addresses
    - Ambient value and explicit values
    - URL generation process
    - Problems with route value invalidation
- Parse URL paths with LinkParser
- Configure endpoint metadata
- Host matching in routes with RequireHost
- Route groups
- Performance guidance for routing
    - Potentially expensive routing features
    - Guidance for large route tables
- Guidance for library authors
