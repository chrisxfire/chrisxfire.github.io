---
title: notes > asp.net > web apps > mvc > views > view components
date: 2023-05-02T00:00:00-06:00
draft: false
weight: 1
---

From Pluralsight/ASP.NET Core 6 Fundamentals

# Overview
View components are view content that does require code to execute in order to render.
- They only display partial content.  They consist of a class and a view (much like a Controller and a View).
- They have their own code that executes to render content.
- They support dependency injection.
- They have a "code part" placed in `/Components/ViewComponentName.cs`
- They have a "view part" placed in `/Shared/Components/ViewComponentName/Default.cshtml`

# Creating a View Component
Three approaches:
1. A class that derives from `ViewComponent`
2. A class decorated with the `[ViewComponent]` attribute
3. A class suffixed with `ViewComponent`

Approach #1:
```cs
// ViewComponent classes must be public, non-abstract, and non-nested:
public class ShoppingCartSummary : ViewComponent
{
    // functionality to execute must be placed in this method:
    public IViewComponentResult Invoke()
    {
        return View(model);
    }
}
```
# Using a View Component
Via Component's InvokeAsync method:
```cs
@await Component.InvokeAsync("ShoppingCartSummary");
```

Via a tag helper:
```html
<vc:shopping-cart-summary></vc:shopping-cart-summary>
```
