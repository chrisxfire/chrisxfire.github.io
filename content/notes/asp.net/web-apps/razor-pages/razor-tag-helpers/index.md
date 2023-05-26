---
title: "notes > asp.net > web apps > razor pages > razor tag helpers"
date: 2023-03-20T00:00:00-06:00
draft: false
---

# Overview
Tag Helpers extend standard HTML elements.  They provide extra server-side attributes for an HTML element.

# Partial Tag Helper
Asynchronously renders a partial view.  
Note that the name attribute accepts the partial view's name without its file extension:
```html
<partial name="_ValidationScriptsPartial" />
```

This is equivalent to Razor HTML Helper syntax:
```cs
@{await Html.RenderPartialAsync("_ValidationScriptsPartial");}
```

# Label Tag Helper
Extends the HTML `<label>` element:
<label asp-for="NewPizza.Name" class="control-label"></label>

The asp-for attribute accepts a PageModel property.  The value of the PageModel's Name property will be rendered as the content for the <label> element.

Input Tag Helper
Extends the HTML <input> element:
<input asp-for="NewPizza.Name" class="form-control" />

It renders this HTML:
<input name="NewPizza.Name" class="form-control" id="NewPizza_Name" type="text" value="" data-val-required="The Name field is required." data-val="true">

This helper:
	• Evaluates NewPizza.Name property
	• Adds an id and name HTML attribute based on that property
	• Sets the input type.  For example, if the property's type was bool, it would set the input type as checkbox.
	• Provides client-side validation via jQuery based on the model's data annotation attributes from the PageModel.
	• If client-side validation succeeded, it prompts the Razor engine to perform further server-side validation.

Validation Summary Tag Helper
Displays a validation message for a single property:
<divasp-validation-summary="All"></div>

It renders this HTML:
<input name="NewPizza.Price" class="form-control" id="NewPizza_Price" type="text" value="" data-val-required="The Price field is required." data-val="true" data-val-range-min="0.01" data-val-range-max="9999.99" data-val-range="The field Price must be between 0.01 and 9999.99." data-val-number="The field Price must be a number.">
