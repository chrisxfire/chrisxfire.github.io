---
title: httpcontext
date: 2023-01-08T00:00:00-06:00
draft: false
weight: 1
---

# [Overview](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/use-http-context?view=aspnetcore-7.0)  

`HttpContext` encapsulates all information about an HTTP request and response.
- Initialized when HTTP request is received
- Accessible by middleware and app frameworks

`HttpContext` <r>is not thread safe</r>.

# `HttpRequest`
Accessed via `HttpContext.Request`.
- Initialized when HTTP request is received
- Mutable
	
Common members:
- `Path`, `Method`, `Headers`
- `RouteValues` — a collection of route values; set when request is matched to a route
- `Query` — a collection of query values parsed from `QueryString`
- `ReadFormAsync()` — reads request body as a form and returns a form values collection
    - See also:  [Prefer `ReadFormAsync` over `Request.Form`](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/best-practices?view=aspnetcore-7.0#prefer-readformasync-over-requestform)
- `Body` — a Stream for reading the request body

## `HttpRequest.Headers`
Access headers in this collection by either:
- Providing header name to indexer:  `request.Headers["x-some-custom-header"]`
- Using its properties:  `request.Headers.UserAgent`

## `HttpRequest.Body`
Allows request body to be read with Stream:
```cs
context.Request.Body.CopyToAsync(writeStream);
```
A request body can only be read once.
To read multiple times, use the `EnableBuffering` extension method:
```cs
context.Request.EnableBuffering() // must be called before reading request body
await ReadRequestBody(context.Request.Body); // read the body
context.Request.Body.Position = 0; // rewind the request body
```

# `HttpResponse`
Accessed via `HttpContext.Response`.
Used to set information on the HTTP response sent back to the client.

Common members:
- `StatusCode`, `ContentType`, `Headers` (all of these must be set before writing to the response body)
- `Body` — a Stream for writing the response body

Responses are started by flushing response body or calling `HttpResponse.StartAsync`.
Use `HttpResponse.HasStarted` to check for start.

## `HttpResponse.Headers`
Access headers in this collection by either:
- Providing header name to indexer:  response.Headers.CacheControl = "no-cache";
- Using its properties:  response.Headers["x-some-custom-header"] = "custom value";

## `HttpResponse.Body`
Allows response body to be written with `Stream`:
```cs
await using var fileStream = File.OpenRead(filePath);
await fileStream.CopyToAsync(context.Response.Body);
```

## response trailers
HTTP/2 and HTTP/3 support response trailers — headers sent with the response after the body is complete.
To set trailers, use `AppendTrailer`:
```cs
if (response.SupportsTrailers())
    response.AppendTrailer("trailername", "TrailerValue");
```

# `HttpContext.RequestAborted`
A cancellation token.  Pass to long-running tasks so that they can cancel if a request is aborted (like a database query).  
Do not use on request body read or write operations.

# `HttpContext.Abort()`
Triggers `HttpContext.RequestAborted` cancellation token and send notification to client.  
Does not trigger an HTTP response 400 (error).

# `HttpContext.User`
Gets or sets the user, represented by `ClaimsPrincipal`, for the request.

# `HttpContext.Features`
A collection of feature interfaces for the current request.  
Mutable even within the context of a request (so middleware can change it).
```cs
var feature = httpContext.Features.Get<IHttpMinRequestBodyDataRateFeature>(); // Get a feature from the collection
if (feature != null)
    feature.MinDataRate = null; // Set MinDataRate to null

```
