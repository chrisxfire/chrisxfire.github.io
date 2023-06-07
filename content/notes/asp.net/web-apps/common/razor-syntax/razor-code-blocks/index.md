---
title: notes > asp.net > web apps > common > razor syntax > razor code blocks
date: 2023-04-24T00:00:00-07:00
draft: false
---

# Overview
Start with `@` and are enclosed in `{ }`.  Unlike expressions, C# code inside code blocks is not rendered:
```html
@{
    var quote = "The future depends on what you do today. - Mahatma Gandhi";
}

<p>@quote</p>

@{
    quote = "Hate cannot drive out hate, only love can do that. - Martin Luther King, Jr.";
}

<p>@quote</p>
```

Declare local functions in code blocks to serve as templating methods:
```cs
@{
    void RenderName(string name)
    {
        <p>Name: <strong>@name</strong></p>
    }

    RenderName("Mahatma Gandhi");
    RenderName("Martin Luther King, Jr.");
}
```
rendered HTML:
```html
<p>Name: <strong>Mahatma Gandhi</strong></p>
<p>Name: <strong>Martin Luther King, Jr.</strong></p>
```

Razor code blocks can transition between C# and HTML…
```html
@{
    var inCSharp = true;
    <p>Now in HTML, was in C# @inCSharp</p>
}
```

…or via the `<text>` tag to render a subsection of a code block as HTML:
```html
@for (var i = 0; i < people.Length; i++)
{
    var person = people[i];
    <text>Name: @person.Name</text>
}
```

Use `@:` to render the rest of an entire line as HTML:
```html
@for (var i = 0; i < people.Length; i++)
{
    var person = people[i];
    @:Name: @person.Name
}
```
