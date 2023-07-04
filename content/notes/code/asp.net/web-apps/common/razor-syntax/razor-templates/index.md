---
title: notes > code > asp.net > web apps > common > razor syntax > razor templates
date: 2023-04-24T00:00:00-07:00
draft: false
---

# Overview
Razor templates allow you to define a UI snippet:   
`@<tag>...</tag>`

# Define a Template
Templates are defined as delegates.  Consider `Pet.cs`:  
```cs
public class Pet
{
    public string Name { get; set; }
}
```

And `RazorTemplate.cshtml`:
```html
@{
    Func<dynamic, object> petTemplate = @<p>You have a pet named <strong>@item.Name</strong>.</p>;

    var pets = new List<Pet>
    {
        new Pet { Name = "Rin Tin Tin" },
        new Pet { Name = "Mr. Bigglesworth" },
        new Pet { Name = "K-9" }
    };
}
```

Render the template like this:
```cs
@foreach (var pet in pets)
{
    @petTemplate(pet)
}
```
Rendered HTML:
```html
<p>You have a pet named <strong>Rin Tin Tin</strong>.</p>
<p>You have a pet named <strong>Mr. Bigglesworth</strong>.</p>
<p>You have a pet named <strong>K-9</strong>.</p>
```

# Use an Inline Razor Template as a Method Argument
Like this:
```html
@using Microsoft.AspNetCore.Html

@functions {
    // this method receives a Razor template:
    public static IHtmlContent Repeat(
        IEnumerable<dynamic> items, 
        int times,
        Func<dynamic, IHtmlContent> template)
    {
        var html = new HtmlContentBuilder();

        foreach (var item in items)
            for (var i = 0; i < times; i++)
                html.AppendHtml(template(item));

        return html;
    }
}
```

Using the `List<Pet>` from the prior example, call the `Repeat` method:
```html
<ul>
    @Repeat(pets, 3, @<li>@item.Name</li>)
</ul>
```
HTML output:
```html
<ul>
    <li>Rin Tin Tin</li>
    <li>Rin Tin Tin</li>
    <li>Rin Tin Tin</li>
    <li>Mr. Bigglesworth</li>
    <li>Mr. Bigglesworth</li>
    <li>Mr. Bigglesworth</li>
    <li>K-9</li>
    <li>K-9</li>
    <li>K-9</li>
</ul>
```
