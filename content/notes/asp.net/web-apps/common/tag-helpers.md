---
title: tag helpers
date: 2023-04-22T00:00:00-07:00
draft: false
weight: 1
---

# overview
Tag Helpers consists of markup code that executes server-side and triggers the execution of code. They can be tags, attributes, or elements.  
They enable server-side code to create and render HTML elements in Razor files.  
They look like standard HTML. They replace HTML Helpers. They have rich IntelliSense support.

# registering tag helpers for use
Tag Helpers can be added in every file that needs to use them or in `_ViewImports.cshtml`:  
`@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers`

# tag helpers to create a link via anchor tag helpers
When this code runs, it will look at the routes in the application and, based on these, generate the correct outgoing link:
This markup…
```html
<a asp-controller="Pie" asp-action="List>
	View Pie List
</a>
```
…results in this HTML:
```html
<a href="/Pie/List">View Pie List</a>
```

# another example
When an image changes, in order to get it rendered in downstream caches or CDNs, the image name must change. This requires changing the name everywhere the image is referenced. `ImageTagHelper` does this for you.

# another example
Consider a Razor view with this model:
```cs
public class Movie
{
    public int ID { get; set; }
    public string Title { get; set; }
    public DateTime ReleaseDate { get; set; }
    public string Genre { get; set; }
    public decimal Price { get; set; }
}
```
In this CSHTML, the `LabelTagHelper` has a `For` property that makes the `asp-for` attribute available on the `<label>` tag:
```html
<label asp-for="Movie.Title"></label>
```

Which renders this HTML:
```html
<label for="Movie_Title">Title</label>
```

ASP.NET Core built-in tag helpers
```
Anchor
Cache
Component
Distributed Cache
Environment
Form
Form Action
Image
Input
Label
Link
Partial
Persist Component State
Script
Select
Textarea
Validation Message
Validation Summary
```
