---
title: directives
date: 2023-04-24T00:00:00-07:00
draft: false
weight: 1
---

# Overview
Directives change the way component markup is parsed or functions.

This CSHTML:
```html
@{
    var quote = "Getting old ain't for wimps! - Anonymous";
}

<div>Quote of the Day: @quote</div>
```

...generates this C# class:
```cs
public class _Views_Something_cshtml : RazorPage<dynamic>
{
    public override async Task ExecuteAsync()
    {
        var output = "Getting old ain't for wimps! - Anonymous";

        WriteLiteral("/r/n<div>Quote of the Day: ");
        Write(output);
        WriteLiteral("</div>");
    }
}
```

## `@attribute`
Adds the given attribute to the class of the generated page or view:
```html
@attribute [Authorize]
```

## `@code`
This only applies to Razor components (`.razor`) and allows the component to add C# members:
```cs
@code {
    // C# members (fields, properties, and methods)
}
```

## `@functions`
Like `@code`, but for Razor pages (`.cshtml`) instead of components:
```cs
@functions {
    // C# members (fields, properties, and methods)
}
```

## `@implements`
Implements an interface in the generated class:
```html
@implements IDisposable

<h1>Example</h1>

@functions {
    private bool _isDisposed;

    ...

    public void Dispose() => _isDisposed = true;
}
```

## @inherits
Provides full control of the class the view inherits.

For this custom Razor page type:
```cs
using Microsoft.AspNetCore.Mvc.Razor;

public abstract class CustomRazorPage<TModel> : RazorPage<TModel>
{
    public string CustomText { get; } = 
        "Gardyloo! - A Scottish warning yelled from a window before dumping" +
        "a slop bucket on the street below.";
}
```
The `CustomText` is displayed in a view:
```html
@inherits CustomRazorPage<TModel>

<div>Custom text: @CustomText</div>
```

Which renders this HTML:
```html
<div>
    Custom text: Gardyloo! - A Scottish warning yelled from a window before dumping
    a slop bucket on the street below.
</div>
```

`@inherits` can also be used in a `_ViewImports.cshtml` file.

## `@inject`
Enables the Razor Page to inject a service from the service container into a view.

## `@layout`
Only applies to Razor components (`.razor`).  See Blazor layouts.

## `@model`
Only applies to MVC views and Razor Pages (not Razor Components).  
Specifies the type of the model passed to a view or page:

`Views/Account/Login.cshtml`
```html
@model LoginViewModel
```

The class that's generated inherits from `RazorPage<LoginViewModel>`:
```cs
public class _Views_Account_Login_cshtml : RazorPage<LoginViewModel>
```

Razor exposes a `Model` property for accessing the model passed to the view:
```html
<div>The Login Email: @Model.Email</div>
```

Without the `@model` directive being used, the `Model` property is of type `dynamic.`

## `@namespace`
Sets the namespace of the class of the generated Razor page, MVC view, or Razor component.  
Sets the root if derived namespaces of pages, views, or components classes:  

If `Pages/_ViewImports.cshtml` contains `@namespace Hello.World`:
| Page | Namespace |
|------|-----------|
| Pages/Index.cshtml | Hello.World |
| Pages/MorePages/Page.cshtml | Hello.World.MorePages |
| Pages/MorePages/EvenMorePages/Page.cshtml | Hello.World.MorePages.EvenMorePages |

If `EvenMorePages` folder has its own imports file with `@namespace Another.Planet`:
| Page | Namespace |
|------|-----------|
Pages/Index.cshtml | Hello.World
Pages/MorePages/Page.cshtml | Hello.World.MorePages
Pages/MorePages/EvenMorePages/Page.cshtml | Another.Planet

## `@page`
In a `cshtml` file, indicates this is a Razor page.  
In a `razor` file, specifies this component should handle requests directly.

## `@section`
Only applies to MVC views and Razor Pages.  
Use in conjuction with layouts to enable views or pages to render content in different parts of the HTML page.  See Layout.

## `@using`
Adds the C# using directive to the generated view:
```html
@using System.IO
@{
    var dir = Directory.GetCurrentDirectory();
}
<p>@dir</p>
```
