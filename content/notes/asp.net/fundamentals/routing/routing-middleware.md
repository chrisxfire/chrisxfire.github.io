---
title: routing middleware
date: 2023-04-20T00:00:00-06:00
draft: false
weight: 1
---

# overview
`UseRouting` — adds route matching to the pipeline; looks at endpoints defined in the app and selects the best match.
- `UseRouting` works by calling the SetEndpoint method to attach the endpoint to the current context.
	
`UseEndpoints` — adds endpoint execution to the pipeline; runs the delegate associated with each the selected endpoint.
- `UseEndpoints` is terminal when a match is found.
- `UseEndpoints` uses GetEndpoint to retrieve the endpoint and then invokes its RequestDelegate property.

`WebApplicationBuilder` configures `UseRouting` and `UseEndpoints`.

# endpoints
- Endpoints in ASP.NET are executable (have a `RequestDelegate`), extensible (have a `Metadata` collection), selectable (with routing information), and enumerable (the collection of endpoints can be listed from `EndpointDataSource` in DI).
- Endpoints that can be matched and executed are configured in `UseEndpoints.` 

To connect ASP.NET framework features to the routing system use:
- `MapRazorPages` for Razor Pages
- `MapControllers` for controllers
- `MapHub<T>` for SignalR
- `MapGrpcService<T>` for gRPC

## route templates
Route templates configure how an endpoint is matched.  Consider:
```cs
app.MapGet("/hello/{name:alpha}", (string name) => $"Hello {name}!");
```
- `/hello/{name:alpha}` is the route template.  This templates matches `/hello/` followed by a sequence of alphabetic characters.
- `alpha` is a route constraint.
- `name` binds the second segment of the URL path to the name parameter and stores it in `HttpRequest.RouteValues`.

## endpoint metadata
Consider:
```cs
app.UseAuthentication();
app.UseAuthorization();

app.MapHealthChecks("/healthz").RequireAuthorization(); // This endpoint is chained with RequireAuthorization.  The endpoint now contains metadata.
app.MapGet("/", () => "Hello World!");
```
Metadata can be of any .NET type and can be processed by routing-aware middleware.

## Terminal Middleware vs. Routing Endpoints
Consider:
```cs
// Approach 1: Terminal Middleware.
app.Use(async (context, next) =>
{
    if (context.Request.Path == "/") // When a match is found…
    {
        await context.Response.WriteAsync("Terminal Middleware."); // …execute some functionality…
        return; // …and return to terminate.
    }

    await next(context);
});

app.UseRouting();

// Approach 2: Routing.
app.MapGet("/Routing", () => "Routing."); // Endpoints are always terminal.
```
Other considerations:
- Positioning  —  Terminal middleware can be positioned anywhere in the pipeline.  Routing endpoints will execute wherever `UseEndpoints` is called.
- Matching  —  Terminal middleware allows for custom matching logic.
- Interfacing with other middleware  —  Routing endpoints interface automatically with other middleware like `UseAuthorization` and `UseCors.`  Terminal middleware requires manual interfacing.

Prefer routing endpoints over terminal middleware.
