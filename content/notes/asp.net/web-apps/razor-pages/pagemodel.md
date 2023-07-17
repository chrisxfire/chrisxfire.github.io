---
title: notes > asp.net > web apps > razor pages > pagemodel
date: 2023-03-20T00:00:00-06:00
draft: false
weight: 1
---

# PageModel
Razor Pages use a C# class called `PageModel` to: 
- define data properties and associated operations for that model's Razor page
- define page handlers (like `OnGet`) for requests sent to that page

`PageModel` supports keeping all page-specifc logic and properties in their own namespace & directory.

## A Page with a PageModel
`Pages/Index2.cshtml`
```html
@page
@using RazorPagesIntro.Pages
@model Index2Model

<h2>Separate page model</h2>
<p>
    @Model.Message
</p>
```

That page's code-behind:
`Pages/Index2.cshtml.cs`
```cs
using Microsoft.AspNetCore.Mvc.RazorPages;
using Microsoft.Extensions.Logging;
using System;

namespace RazorPagesIntro.Pages
{
    public class Index2Model : PageModel
    {
        public string Message { get; private set; } = "PageModel in C#";

        public void OnGet()
        {
            Message += $" Server time is { DateTime.Now }";
        }
    }
}
```

# Page Handlers
Page handlers are invoked automatically when a request is received.  They separate logic from presentation.  
Page handlers are defined in the `PageModel` class file of the associated Razor page.

## Example
```cs
public Order? Order { get; set; }

public IActionResult OnGet() // Async version also exists
{
    Order = dbContext.Orders.First();
    
    return Page();
}
```

## Example 2
```cs
using Microsoft.AspNetCore.Mvc;
using Microsoft.AspNetCore.Mvc.RazorPages;

namespace RazorPagesPizza.Pages;

public class PizzaModel : PageModel
{
    // This binds the model to the PageModel.
    [BindProperty]
    public Pizza NewPizza { get; set; }

    // An HTTP GET page handler
    public void OnGet()
    {
    }
}
```

# Model Binding and Validation
You can bind the model to the `PageModel` using the `BindProperty` attribute:
```cs
[BindProperty]
public Pizza NewPizza { get; set; }
```

Both model binding and validation occur before the execution of a page handler automatically in ASP.NET Core.
This means you only need to verify the outcome of the validation:
```cs
if (!ModelState.IsValid)
{
    // If ModelState is invalid, display the pizza page again to the user.
    return Page();
}
```

# Complete Model
```cs
public class PizzaModel: PageModel
{
    
	[BindProperty]
	public Pizza NewPizza { get; set; } = new();

	public void OnGet()
	{
		pizzas = PizzaService.GetAll();
	}

	public async Task<IActionResult> OnPostAsync()
	{
		if (!ModelState.IsValid)
		{
			return Page();
		}
		
		PizzaService.Add(NewPizza);
	
		return RedirectToAction("Get");
	}
	
	public async Task<IActionResult> OnPostDelete(int id)
	{
	    PizzaService.Delete(id);
	
	    return RedirectToAction("Get");
	}
	
}
```
