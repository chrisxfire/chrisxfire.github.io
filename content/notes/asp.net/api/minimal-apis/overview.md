---
title: overview
date: 2023-09-27T00:00:00-06:00
draft: true
weight: -1
---

# Abstract [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/minimal-apis/overview?view=aspnetcore-7.0)]  
> TODO: Finish adding notes from the above documentation.

# Middleware Sequencing in Minimal API Apps [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/minimal-apis/webapplication?view=aspnetcore-7.0)]  
> TODO: Finish adding notes from the above documentation.

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