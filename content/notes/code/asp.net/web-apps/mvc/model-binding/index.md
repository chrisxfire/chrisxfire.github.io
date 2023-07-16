---
title: notes > code > asp.net > web apps > mvc > model binding
date: 2023-05-03T00:00:00-06:00
draft: false
weight: 1
---

# Model Binding
Model binding converts client request data (like form values, route parameters, query string parameters, HTTP headers) into objects that the controller can handle.  This data is passed as parameters to the controller's action methods:
```cs
public async Task<IActionResult> Login(LoginViewModel model, string returnUrl = null) { ... }
```

Model binding works for primitives (`int`, `string`, `bool`) and complex types (`objects`).

# Example
Consider an action method that requires an `id` of type `int`:  
```cs
public ViewResult Detail(int id)
```

Model binding will try to find the value for this parameter:  
```
/Pie/Detail/1
```
It does this by using model binders.  Model binders are components which provide values from a certain location within a request:  form data, route variables, or query strings.  In this case, the route variable model binder will provide the needed value.
