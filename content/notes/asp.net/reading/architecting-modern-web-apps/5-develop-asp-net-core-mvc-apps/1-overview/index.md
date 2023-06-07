---
title: notes > asp.net > reading > architecting modern web apps > 5 develop asp net core mvc apps > 1 overview
date: 2023-04-14T00:00:00-06:00
draft: false
---

# MVC and Razor Pages
Razor Pages are built into ASP.NET Core MVC and use the same features for routing, model binding, filters, authorization, etc.  

Comparison:
| Technology  | Organization                                          | Routing                                    | Request Handling   |
| ----------- | ----------------------------------------------------- | ------------------------------------------ | ------------------ |
| MVC         | Separate folders for Controllers, Models, Views, etc. | Attribute-based routing                    | Controller Actions |
| Razor Pages | A single folder (/Pages)                              | Route based relative to location in folder | Handlers           |

In Visual Studio:
| Project template | Uses            | Missing                       | Use for  |
| ---------------- | --------------- | ----------------------------- | -------- |
| Web API          | MVC controllers | /Views, /Pages — can be added | Web APIs |
| Web App          | Razor Pages     | /Views, /Pages — can be added | Web apps |

## Razor Pages
The default approach for new web apps in Visual Studio.  Razor Pages encapsulates server-side logic for a given logical "page" in a web application.

A Razor Page's  page model combines responsibilities of an MVC controller and a viewmodel.  Instead of handling requests with controller actions, page model handlers like `OnGet()` are executed and render their associated page.

# Mapping Requests to Responses
Concepts:
- Conventional routes (applied in middleware pipeline)
- Attribute routes (applied to controllers and actions)
- Content negotiation allows requests to specify how responses should be formatted (JSON, XML, etc)

When a request is matched to a route, but before the action is called, ASP.NET Core MVC will perform model binding and model validation on the request.
- Model binding converts incoming HTTP data into .NET types specified as parameters of the action method to be called.
  - If the action method expects an int id, model binding will look for values in the route itself, query strings, or posted forms to attempt to provide it.
- Model validation uses optional attributes on the model type to ensure the model object conforms to certain data requirements.

## Preventing Large Controllers
The mediator design pattern reduces coupling between classes while allowing communication between them.
Use the MediatR Nuget package.
