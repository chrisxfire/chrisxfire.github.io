---
title: notes > asp.net > web apps > mvc > models
date: 2023-05-03T00:00:00-06:00
draft: false
weight: 1
---

From Pluralsight/ASP.NET Core 6 Fundamentals

# Model Responsibilities
A group of classes that make up domain data — POCO classes.  
Also contains classes that manage the data — repository classes.  
Hides details of managing the data.  

Repository classes abstract away how data is persisted; this allows other code to use these classes without this concern.
```cs
public interface IPieRepository {
	IEnumerable<Pie> AllPies { get; }
	Pie GetPieById(int pieId);
}
```

Represents the state of the application and any business logic or operations it should perform.

Strongly-typed views use `ViewModel` types that contain the data to display on that view.  The controller creates and populates these `ViewModel` instances from the model.

A Pie Model:
```cs
public class Pie
{
	public int PieId { get; set; }
	public string Name { get; set; }
	…
}
```

# Validation
## `ModelState`
`ModelState` is an output of model binding.  `ModelState` holds any errors that occurred during model binding.  If errors occurred, `ModelState.IsValid` returns false.  On a controller action:
```cs
public async Task<IActionResult> Login(LoginViewModel model, string returnUrl = null)
{
    if (ModelState.IsValid)
    {
        // work with the model
    }
    // At this point, something failed, redisplay form
    return View(model);
}
```
`ModelState`'s built-in validation is very basic.  In order to more robustly validate that an object complies with a model, use model validation (see below).

## Getting `ModelState`'s `ValidationState`

## Adding Errors to `ModelState`
`ModelState` can also hold additional errors you add, such as business logic errors:
```cs
if (_shoppingCart.ShoppingCartItems.Count == 0)
    ModelState.AddModelError("", "Your cart is empty, add some pies first");
```

# Model Validation
The model can be decorated with data annotation validation attributes.  These are checked on the client side before values are posted to the server, and on the server before the controller action is called:
```cs
using System.ComponentModel.DataAnnotations;

public class LoginViewModel
{
    [Required(ErrorMessage = "Enter an email address"]
    [EmailAddress]
    public string Email { get; set; }

    [Required]
    [DataType(DataType.Password)]
    public string Password { get; set; }

    [Display(Name = "Remember me?")]
    public bool RememberMe { get; set; }
}
```
| Validation Attribute | Validates… |
|----------------------|------------|
`Required` | that a value is provided
`StringLength(int)` | that a string's length is no longer than specified
`Range` | that a value is within a range
`RegularExpression` | that a value satisfies a regex
`EmailAddress` | that the value is a valid email address
`PhonenNumber` | that the value is a valid phone number

# Validation Summary Tag Helper
This tag helper is used to display model validation errors to the user, usually at the top of the page:
```html
<form asp-action="Checkout" method="post>
	<div asp-validation-summary="All" class="text-danger">
	</div>
</form>
```

# Validation Message Tag helper
This tag helper is used to display model validation errors to the user at the field where the error occurred:
```html
<div class="col-12">
	<label asp-for="Email" class="form-label"></label>
	<input asp-for="Email" class="form-control" />
	<span asp-validation-for="Email" class="text-danger"></span>
</div>
```
