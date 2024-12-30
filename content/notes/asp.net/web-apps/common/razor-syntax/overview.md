---
title: overview
date: 2023-03-24T00:00:00-07:00
draft: false
weight: -1
---

# abstract
Razor is a syntax for combining HTML markup with C# code.  
Razor pages are `cshtml` files.  
Razor components (used in Blazor apps) are `.razor` files.  

# rendering html
HTML is the default Razor language.

## razor syntax
Razor uses the `@` symbol to transition from C# to HTML.  It evaluates C# expressions and renders them in the HTML output.  
When `@` precedes a Razor reserved keyword, it transitions into Razor-specific markup.  Otherwise, it transitions to HTML.

To escape an `@` symbol, use two: `<p>@@username</p>`  

HTML attributes and content that contain email addresses do not treat the @ symbol as a transition character:
```html
<a href="mailto:Support@contoso.com">Support@contoso.com</a>
```

## scalable vector graphics
Razor supports SVC `foreignObject` elements:
```html
@{
    string message = "foreignObject example with Scalable Vector Graphics (SVG)";
}

<svg width="200" height="200" xmlns="http://www.w3.org/2000/svg">
    <rect x="0" y="0" rx="10" ry="10" width="200" height="200" stroke="black" 
        fill="none" />
    <foreignObject x="20" y="20" width="160" height="160">
        <p>@message</p>
    </foreignObject>
</svg>
```

# conditional attribute rendering
Razor ignores attributes that are not needed.  If the value passed in is null or false, the attribute is not rendered.

# comments
Razor supports three types of comments:
```cs
@{
    /* C# comment */
    // Another C# comment
}
```
```html
<!-- HTML comment -->
```

To prevent even HTML comments from being rendered, wrap them in `@*` and `*@`.

# html encoding
C# expressions that…  
…evaluate to a string --> are HTML-encoded  
…evaluate to `IHtmlContent` --> are rendered directly through IHtmlContent.WriteTo  
…do not evaluate to `IHtmlContent` --> are converted to a string by ToString and encoded before they are rendered  

This:  `@("<span>Hello World</span>")`
Renders to:  `&lt;span&gt;Hello World&lt;/span&gt;`

This:  `@Html.Raw("<span>Hello World</span>")`
Renders to:  `<span>Hello World</span>`

# seeing the class that razor generates for a view
By default, these are not emitted.  To enable, in `csproj`:  
```xml
<PropertyGroup>
    <EmitCompilerGeneratedFiles>true</EmitCompilerGeneratedFiles>
</PropertyGroup>
```

Build the project in Debug configuration and find the classes in `/obj/Debug/net6.0/generated`.

# Auto-Imports
ASP.NET Core web templates use these auto imports:
```cs
using System;
using System.Collections.Generic;
using System.Linq;
using System.Threading.Tasks;
using Microsoft.AspNetCore.Mvc;
using Microsoft.AspNetCore.Mvc.Rendering;
using Microsoft.AspNetCore.Mvc.ViewFeatures;
```
