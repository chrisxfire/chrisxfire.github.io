---
title: application model
date: 2023-08-20T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/application-model?view=aspnetcore-7.0

ASP.NET Core MVC defines an *application model* that represents the components of an MVC app. It includes both abstract interfaces and concrete implementation classes that describe an MVC application. It results from MVC discovering the app's controllers, actions, action parameters, routes, and filters. By modifying the model, an app can follow different conventions than the default MVC behavior.

The application model has this structure:
```
ApplicationModel
    └── Controllers (ControllerModel)
        └── Actions (ActionModel)
            └── Parameters (ParameterModel)
```

See the documentation for more information.

# Using `ApiExplorer` to Document an App
The application model exposes an `ApiExplorerModel` property at each level that can be used to traverse the app's structure. This can be used to generate help pages with tools like Swagger. ApiExplorer has an IsVisible property that can be used to determine which parts of the app's model are exposed:
```cs
using Microsoft.AspNetCore.Mvc.ApplicationModels;

namespace AppModelSample.Conventions
{
    public class EnableApiExplorerApplicationConvention : IApplicationModelConvention
    {
        public void Apply(ApplicationModel application)
        {
            application.ApiExplorer.IsVisible = true;
        }
    }
}
```