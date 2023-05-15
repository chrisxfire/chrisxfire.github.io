---
title: "notes > asp.net > core > overview"
date: 2023-05-14T00:00:00-06:00
draft: false
---

# Overview
ASP.NET Core web applications function as console applications.
By default, they use Kestrel as the web server.

## Web App Frameworks
- Server-rendered Apps
    - ASP.NET Core Razor Pages
    - ASP.NET Core MVC
    - Blazor Server
- Client-rendered Apps
    - Blazor WASM
    - ASP.NET Core SPA (w/Angular or React)
- Hybrid
- Web APIs
    - Controller-based API
    - Minimal API
- Real-time Apps
- RPC Apps
    - gRPC

# Fundamentals (Common to all ASP.NET app models)
## Project Structure
- `Pages/` — Razor pages and supporting files.
    - `.cshtml` file with HTML markup with C# code using Razor syntax
    - `.cshtml.cs` C# code that handles page events
    - `_Layout.cshtml` configures UI elements common to all pages; sets up nav menu at top of page and copyright at bottom of page.
- `wwwroot/`
    - Static assets (HTML, JS, CSS files)
- `appsettings.json`
    - Configuration data.
- `Program.cs`
    - Services are configured.
    - Request handling pipeline (middleware) is defined.
- `Models/`
    - Add this to hold the data models.

# Dependency Injection
- Makes configured services available throughout an app.
- Services are added to the DI container with `WebApplicationBuilder.Services`.
- When `WebApplicationBuilder` is instantiated, many framework-provided services are added.

# Middleware
The request handling pipeline is composed of a series of middleware components.  
Each component performs operations on an `HttpContext` and either:
1. Invokes the next middleware in the pipeline, or;
2. Terminates the request.

Middleware components are added to the pipeline with the `UseFeature` convention:  
```cs
// Configure the HTTP request pipeline.
if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    app.UseHsts();
}

app.UseHttpsRedirection(); // Redirect HTTP requests to HTTPs
app.UseStaticFiles();

app.UseAuthorization();
```
# Host
ASP.NET Core apps build a Host on startup.  The host encapsulates all of the app's resources:
- An HTTP server
- Middleware
- Logging
- DI services
- Configuration

## 3 different hosts
- *.NET Minimal Host* (recommended; used by default in templates)
- *.NET WebApplication Host*
- *.NET Generic Host* (similar to Minimal); allows other types of apps (not web apps) to use framework extensions like logging, DI, configuration, etc.
- *ASP.NET Core Web Host* (deprecated)

## Instantiate a host
```cs
WebApplication app = builder.Build();
```
The host is instantiated with these default options:
- Kestrel web server w/IIS integration
- Configuration from `appsettings.json`, environment variables, command line arguments, other.
- Logging output to console and debug providers.

# Servers
ASP.NET Core apps use an HTTP server to listen for HTTP requests.  In Windows, the options are:
- Kestrel—cross-platform; can run as a reverse proxy; can run as a public-facing edge server exposed to the Internet.
- IIS HTTP Server—ASP.NET Core app and IIS run in the same process.
- HTTP.sys

# Configuration
See also:  [Configuration in ASP.NET Core | Microsoft Learn](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/?view=aspnetcore-7.0)
Default configuration sources:  appsettings.json, environment variables, command line arguments, more.
- Values from environment variables override those in appsettings.json.

For confidential configuration data, use [Secret Manager](https://docs.microsoft.com/en-us/aspnet/core/security/app-secrets?view=aspnetcore-6.0#secret-manager).
For production secrets, use [Azure Key Vault](https://docs.microsoft.com/en-us/aspnet/core/security/key-vault-configuration?view=aspnetcore-6.0).

# Options
See also:  [Options pattern in ASP.NET Core | Microsoft Learn](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/options?view=aspnetcore-7.0)

# Environments
See also:  [Use multiple environments in ASP.NET Core | Microsoft Learn](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/environments?view=aspnetcore-7.0)
ASP.NET Core supports environments such as Development, Staging, and Production.  
`ASPNETCORE_ENVIRONMENT` environment variable specifies the environment in which the app is running.

This example configures the exception handler and HSTS when not running in Development environment:
```cs
if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    app.UseHsts();
}
```
# Make HTTP Requests
An implementation of `IHttpClientFactory` is available for creating HttpClient instances.
Register and configure one client for calling an API.  Register and configure the default client for all other purposes.

# Content Root
The base path for:  the executable hosting the app (`.exe`); compiled assemblies (`.dll`); content files (Razor (`.cshtml`, `.razor`); configuration files (`.json`, `.xml`); data files (`.db`)); the web root (`wwwroot` folder).

During development, content root is the project's root directory.
Content root can be changed when building the host.

# Web Root
The base path for public, static resource files:  Stylesheets, JavaScript, Images.
Default path = `*content root*/wwwroot`.
Web root can be changed when building the host.
