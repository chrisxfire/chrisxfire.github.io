---
title: layout
date: 2023-03-24T00:00:00-07:00
draft: false
weight: 1
---

# Overview
<img src=layout.png width=500 height=250>  

The default layout file is `Pages/Shared/_Layout.cshtml` (Razor Pages) and `Views/Shared/_Layout.cshtml` (MVC).

# Referencing a Layout
Razor views have a `Layout` property that can be used by individual views to reference a layout it wants to use:

`SomeView.cshtml`
```cs
@{
    // this could be a full path but ASP.NET Core MVC knows to check /Views/Shared for a .cshtml file:
    Layout = "_Layout"; 
}
```

Alternatively, use a `ViewStart` file placed at `/Views/_ViewStart.cshtml` with this same code which will then be used automatically by every View.

# Defining a Layout
## RenderBody
Every layout must call `RenderBody.`  This defines where the contents of the view will be rendered:  
`_Layout.cshtml`
```html
<!-- ... -->
    <div class="container body-content">
        @RenderBody()
        <hr />
        <footer>
            <p>&copy; 2018 - WebApplication1</p>
        </footer>
    </div>
<!-- ... -->

## Sections (`RenderSection`)
Optionally, a layout can reference one or more sections that provide a way to organize where certain page elements should be placed:

```html
<script type="text/javascript" src="~/scripts/global.js"></script>

@RenderSection("Scripts", required: false) // defines this setion as optional; if defined as required
                                    // and not found, an exception is thrown
```

Views specify the content to be rendered within a section using @section Razor syntax:
```html
@section Scripts { // scripts/main.js is added to the scripts section on this view:
        <script type="text/javascript" src="~/scripts/main.js"></script>
}
```

The body and every section in a Razor page must be either rendered or ignored.  Call `IgnoreBody` and `IgnoreSection` as needed.
