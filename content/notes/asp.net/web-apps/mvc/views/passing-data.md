---
title: "notes > asp.net > web-apps > mvc > views > passing data"
date: 2023-03-20T00:00:00-06:00
draft: false
---

From Pluralsight/ASP.NET Core 6 Fundamentals

# ViewModels
## ViewModels (strongly typed)
If you specify a model type in the view, we call this a `ViewModel`.  An instance of the `ViewModel` is passed to the view from the action.

ViewModels are either stored in `Models/` or `Viewmodels/`.

`Address.cs`
```cs
namespace WebApplication1.ViewModels
{
    public class Address
    {
        public string Name { get; set; }
        public string Street { get; set; }
        public string City { get; set; }
        public string State { get; set; }
        public string PostalCode { get; set; }
    }
}
```

Define a model with `@model`.  Use the model with `@Model`:
```html
@model WebApplication1.ViewModels.Address

<h2>Contact</h2>
<address>
    @Model.Street<br>
    @Model.City, @Model.State @Model.PostalCode<br>
    <abbr title="Phone">P:</abbr> 425.555.0100
</address>
```

The controller passes the viewmodel instance to the view as a parameter:  
`.cs`
```cs
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";

    var viewModel = new Address()
    {
        Name = "Microsoft",
        Street = "One Microsoft Way",
        City = "Redmond",
        State = "WA",
        PostalCode = "98052-6399"
    };

    return View(viewModel);
}
```

## `ViewData` (weakly typed)
Since `ViewData` (and `ViewBag`) are dynamically resolved at runtime, they don't offer compile-time type checking.

`ViewData` is a `ViewDataDictionary` object accessed through string keys.  `ViewData` object values must be cast to specific types when extracted.

`.cs`
```cs
public IActionResult SomeAction()
{
    ViewData["Greeting"] = "Hello";
    ViewData["Address"]  = new Address()
    {
        Name = "Steve",
        Street = "123 Main St",
        City = "Hudson",
        State = "OH",
        PostalCode = "44236"
    };

    return View();
}
```

`.cshtml`
```html
@{
    // Since Address isn't a string, it requires a cast.
    var address = ViewData["Address"] as Address;
}

@ViewData["Greeting"] World!

<address>
    @address.Name<br>
    @address.Street<br>
    @address.City, @address.State @address.PostalCode
</address>
```

# `[ViewData]` Attribute
Properties on controllers or Razor Page models marked with `[ViewData]` have their values stored and loaded from the `ViewDataDictionary`:

`.cs`
```cs
public class HomeController : Controller
{
    [ViewData]
    public string Title { get; set; }

    public IActionResult About()
    {
        Title = "About Us";
        ViewData["Message"] = "Your application description page.";

        return View();
    }
}
```

`.cshtml`
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>@ViewData["Title"] - WebApplication</title>
    ...
```

# `ViewBag`
`ViewBag`s are a way to pass data to a view.

`ViewBag` is a `Microsoft.AspNetCore.Mvc.ViewFeatures.Internal.DynamicViewData` object:
- It allows creation via dot notation (`@ViewBag.SomeKey = value` or `object`)
- It does not require casting
- It is simpler to check for nulls (`@ViewBag.Person?.Name`)

`.cs`
```cs
public IActionResult SomeAction()
{
    // since ViewBag is dynamic, you can add properties of any name to the object
    ViewBag.Greeting = "Hello"; 
    ViewBag.Address  = new Address()
    {
        Name = "Steve",
        Street = "123 Main St",
        City = "Hudson",
        State = "OH",
        PostalCode = "44236"
    };

    return View();
}
```

`.cshtml`
```html
// the View can then access the data in its properties:
@ViewBag.Greeting World! 

<address>
    @ViewBag.Address.Name<br>
    @ViewBag.Address.Street<br>
    @ViewBag.Address.City, @ViewBag.Address.State @ViewBag.Address.PostalCode
</address>
```