---
title: overview
date: 2023-09-27T00:00:00-06:00
draft: false
weight: -1
---

# Abstract [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/minimal-apis/overview?view=aspnetcore-7.0)]  
Minimal APIs are a simplified approach to building fast HTTP APIs with ASP.NET Core that skip traditional scaffolding and avoid unnecessary controllers. They fluently
declare API routes and actions:

```cs
var app = WebApplication.Create(args);

app.MapGet("/", () => "Hello World!");

app.MapGet("/users/{userId}/books/{bookId}", 
    (int userId, int bookId) => $"The user id is {userId} and book id is {bookId}");

app.Run();
```

# Middleware Sequencing in Minimal API Apps [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/minimal-apis/webapplication?view=aspnetcore-7.0)]  
`WebApplication` adds the following middleware:
| Sequence | Middleware                  | Conditions                                        |
| -------- | --------------------------- | ------------------------------------------------- |
| 1        | `UseDeveloperExceptionPage` | `HostingEnvironment` == "Development"             |
| 2        | `UseRouting`                | Endpoints are configured (like with `app.MapGet`) |
| 3        | `UseEndpoints`              | Endpoints are configured                          |
| 4        | `UseAuthentication`         | `AddAuthentication` is called                     |
| 5        | `UseAuthorization`          | `AddAuthorization` is called                      |

All user-configured middleware and endpoints are added after `UseRouting` (#2) but before `UseEndpoints` (#3).

## Cross-Origin Resource Sharing Middleware (`UseCors`)
If the app requires CORS:
1. Call `UseCors` manually
2. Call `UseAuthentication` manually
3. Call `UseAuthorization` manually

## Running Middleware Before Rout Matching
If middleware must be run before route matching occurs:
1. Call `app.Use((context, next) => { })` for middleware that needs to run first
2. Call `UseRouting` manually

`UseEndpoints` will be called automatically.

## Terminal Middleware
This is middleware that runs if no endpoint handles the request.

When using terminal middleware:
1. Call `UseRouting` manually
2. Call `MapGet` manually
3. Call `UseEndpoints` manually
4. Call the terminal middleware:
    ```cs
    app.Run(context => 
    {
        context.Response.StatusCode = 404;
        return Task.CompletedTask;
    });
    ```