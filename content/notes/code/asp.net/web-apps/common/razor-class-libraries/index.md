---
title: notes > code > asp.net > web apps > common > razor class libraries
date: 2023-03-24T00:00:00-07:00
draft: false
weight: 1
---

# Overview
Razor Class Libraries can contain Razor views, pages, controllers, page models, Razor Components, View components, and data models along with their associated static files.  They can be packaged and reused.

# Creating
Visual Studio project type = `Razor Class Library`
`dotnet new razorclasslib`

ASP.NET Core templates assume RCL content is in `Areas` folder.

## Precedence
When a view, partial view, or Razor Page exists in both the web app and the RCL, the web app takes precedence over (overrides) the one in the RCL.

## RCL Pages layout
To reference RCL content as though it is a part of the web app's `Pages` folder, create the RCL project with this structure:
```
RazorUIClassLib/Pages
RazorUIClassLib/Pages/Shared
```

## Create an RCL with Static Assets
Create a `wwwroot` folder in the class library and include any required files in that folder.
The `dotnet pack` command automatically includes this folder in the package.

## Exclude Static Assets
Add this to `csproj`:
```xml
<PropertyGroup>
  <DefaultItemExcludes>$(DefaultItemExcludes);wwwroot\lib.css</DefaultItemExcludes>
</PropertyGroup>
```

# Using an RCL in a Component
1. Add a project reference from the Component's project to the RCL project
2. Add a `@using` directive either in the Component directly or in `_Imports`
3. (if RCL uses static assets) Bring in the CSS on the hosting page (`index.html` or `host.cshtml`)  
Note the _content prefix that is required when referencing a project other than the current one:
```html
<link href="_content/BethanysPieShopHRM.ComponentsLibrary/leaflet/leaflet.css" rel="stylesheet" />
```

More…
