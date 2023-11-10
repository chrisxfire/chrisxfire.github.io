---
title: controllers
date: 2023-03-21T00:00:00-06:00
draft: false
weight: 1
---

# Overview [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/actions?view=aspnetcore-7.0)]  

A *controller* defines a set of *actions*.  An *action* is a method on a controller which handles *requests*.  Requests are mapped to actions through routing.  
A controller is responsible for initial processing of the request and instantiation of the model.  Business logic should remain in the model.

The controller:
- validates request data 
- takes the result of the model's processing (if any) 
- returns either the appropriate proper view or the result of the API call.

The controller's responsibilities do not include data access or business logic it instead delegates to services handling these concerns.  Business concerns should be represented as services that the controller accesses through DI.

Controllers reside in `Controller/` and inherit from `Microsoft.AspNetCore.Mvc.Controller`.

Controller classes:
- are instantiable
- are usually public
- are suffixed with "Controller"
- have the `[Controller]` attribute

# Approach
If multiple controller actions require the same service, use constructor injection to request the dependencies.
If the service is needed by only a single controller action, use action injection to request the dependency.

# Define a Controller
Public methods on a controller are actions. Parameters on actions are bound to request data and are validated using model binding.  
Validation occurs for everything that's model-bound.  `ModelState.IsValid` is boolean if binding and validating succeeded.  
Actions usually return an `IActionResult` that produces a response.  
- The action method chooses the type of response.
- The `IActionResult` does the responding. 
	
## Controller Helper Methods
There are three types:
1. Methods resulting in an empty response body
    1. HTTP Status Code result types:
        1. `BadRequest()`, `NotFound()`, `Ok()`
    2. Redirect—includes a Location HTTP response header
        1. `Redirect()`, `LocalRedirect()`, `RedirectToAction()`, `RedirectToRoute()`
2. Methods resulting in a non-empty response body with predefined content
    1. View—returns a view which uses a model to render HTML
        1. `return View(customer);`
    2. Formatted Response—returns JSON to represent an object
        1. `return Json(customer)`, `File()`, `PhysicalFile()`
3. Content Negotiation
    1. Applies whenever an action returns an `ObjectResult` type
    2. An action that returns a non-`IActionResult` implementation (like object) also returns a Formatted Response
    3. `BadRequest(modelState)`, `CreatedAtRoute("routename", values, newobject)`, `Ok(value)`
