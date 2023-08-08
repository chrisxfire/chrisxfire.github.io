---
title: list of built in middleware
date: 2023-01-08T00:00:00-06:00
draft: false
weight: 1
---

<style>
    r { color: red }
    o { color: orange }
    g { color: green }
</style>
# [Overview](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/middleware/?view=aspnetcore-7.0#built-in-middleware)
| Middleware | Description | Order |
|------------|-------------|-------|
Authentication | Provides authentication support. | Before HttpContext.User is needed. Terminal for OAuth callbacks.
Authorization | Provides authorization support. | Immediately after the Authentication Middleware.
Cookie Policy | Tracks consent from users for storing personal information and enforces minimum standards for cookie fields, such as secure and SameSite. | Before middleware that issues cookies. Examples: Authentication, Session, MVC (TempData).
CORS | Configures Cross-Origin Resource Sharing. | Before components that use CORS. UseCors currently must go before UseResponseCaching due to this bug.
DeveloperExceptionPage | Generates a page with error information that is intended for use only in the Development environment. | Before components that generate errors. The project templates automatically register this middleware as the first middleware in the pipeline when the environment is Development.
Diagnostics | Several separate middlewares that provide a developer exception page, exception handling, status code pages, and the default web page for new apps. | Before components that generate errors. Terminal for exceptions or serving the default web page for new apps.
Forwarded Headers | Forwards proxied headers onto the current request. | Before components that consume the updated fields. Examples: scheme, host, client IP, method.
Health Check | Checks the health of an ASP.NET Core app and its dependencies, such as checking database availability. | Terminal if a request matches a health check endpoint.
Header Propagation | Propagates HTTP headers from the incoming request to the outgoing HTTP Client requests. | 
HTTP Logging | Logs HTTP Requests and Responses. | At the beginning of the middleware pipeline.
HTTP Method Override | Allows an incoming POST request to override the method. | Before components that consume the updated method.
HTTPS Redirection | Redirect all HTTP requests to HTTPS. | Before components that consume the URL.
HTTP Strict Transport Security (HSTS) | Security enhancement middleware that adds a special response header. | Before responses are sent and after components that modify requests. Examples: Forwarded Headers, URL Rewriting.
MVC | Processes requests with MVC/Razor Pages. | Terminal if a request matches a route.
OWIN | Interop with OWIN-based apps, servers, and middleware. | Terminal if the OWIN Middleware fully processes the request.
Output Caching | Provides support for caching responses based on configuration. | Before components that require caching. 
 |  | UseRouting must come before UseOutputCaching. 
 |  | UseCORS must come before UseOutputCaching.
Response Caching | Provides support for caching responses. This requires client participation to work. Use output caching for complete server control. | Before components that require caching. UseCORS must come before UseResponseCaching. Is typically not beneficial for UI apps such as Razor Pages because browsers generally set request headers that prevent caching. Output caching benefits UI apps.
Request Decompression | Provides support for decompressing requests. | Before components that read the request body.
Response Compression | Provides support for compressing responses. | Before components that require compression.
Request Localization | Provides localization support. | Before localization sensitive components. Must appear after Routing Middleware when using RouteDataRequestCultureProvider.
Endpoint Routing | Defines and constrains request routes. | Terminal for matching routes.
SPA | Handles all requests from this point in the middleware chain by returning the default page for the Single Page Application (SPA) | Late in the chain, so that other middleware for serving static files, MVC actions, etc., takes precedence.
Session | Provides support for managing user sessions. | Before components that require Session.
Static Files | Provides support for serving static files and directory browsing. | Terminal if a request matches a file.
URL Rewrite | Provides support for rewriting URLs and redirecting requests. | Before components that consume the URL.
W3CLogging | Generates server access logs in the W3C Extended Log File Format. | At the beginning of the middleware pipeline.
WebSockets | Enables the WebSockets protocol. | Before components that are required to accept WebSocket requests.
