---
title: notes > code > asp.net > web apps > common > forms
date: 2023-05-03T00:00:00-07:00
draft: false
---

From Pluralsight/ASP.NET Core 6 Fundamentals
# Creating a Form Using Tag Helpers
ASP.NET Core has built-in Tag Helpers for creating forms:
- `Form`
    - `asp-controller` to specify which controller to target on a form's POST action
    - `asp-action` to specify which action to target on a form's POST action
    - `asp-route-*` to create a route where * can be the name of a parameter we want to specify a value for
    - `asp-route` to specify which named route to use
    - `asp-antiforgery` to counter cross-site request forgery attacks
- `Input`
- `Label`
- `Textarea`
- `Select`
- `Validation`

Get the name of the property we want to display via the `asp-for` attribute on the label tag helper:  
`<label asp-for="FirstName"></label>`

…which generates this HTML:
```html
<label for="Firstname">FirstName</label>
```

# Form Tag Helper
The form tag helper enables CSFR attack mitigations by default.
```html
    <!-- trigger the Checkout action on current controller since no other controller specified -->
	<form asp-action="Checkout" 
		 method="post" role="form">
		 <!-- ... -->
	</form>
```
