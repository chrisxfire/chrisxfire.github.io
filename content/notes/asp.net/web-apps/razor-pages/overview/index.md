---
title: "notes > asp.net > web apps > razor pages > overview"
date: 2023-05-03T00:00:00-06:00
draft: false
---

# [Overview](https://learn.microsoft.com/en-us/aspnet/core/razor-pages/?view=aspnetcore-7.0&tabs=visual-studio)

Use Razor Pages for coding page-focused scenarios more productively than using Controllers and Views.

ASP.NET Core Razor Pages can co-exist in the same project with ASP.NET Core MVC.

Project type = ASP.NET Core Web App (`webapp`, `razor`)

# Enabling Razor Pages

Like so:

```cs
// …
builder.Services.AddRazorPages(); // Adds services for Razor Pages to the app
// …
// Routing in Razor Pages is different from MVC.  This method registers Razor Pages as endpoints in IEndpointRouteBuilder:
app.MapRazorPages(); 
app.Run();
```

# A Basic Razor Page

`SomePage.cshtml`

```html
<!-- makes this into an MVC action (it handles requests directly without going through a controller): -->
@page 

<h1>Hello, world!</h1>
<h2>The time on the server is @DateTime.Now</h2>
```

# Add a Razor Page
`dotnet new page --name PageName --namespace Namespace.Pages --output Pages`
Creates `PageName.cshtml` and `PageName.cshtml.cs` in `Pages/`

# Project Structure
`├──Pages/` — Razor Pages and supporting files.  Each Razor Page is a pair of files:  
&emsp;`├──*.cshtml` file (markup with C# using Razor syntax)  
&emsp;`└──*.cshtml.cs` file (the PageModel)  
`├──Pages/Shared/` — Partial views shared across several Razor pages.  
&emsp;`├──_Layout.cshtml` — Common layout elements  
&emsp;`├──_ValidationScriptsPartial.cshtml` — Client-side form input validation, cross-site antiforgery validation, etc  
`├──wwwroot/` — Static asset files (HTML, JavaScript, CSS)  
`└──Program.cs` — The app's main entrypoint.  

# Layouts
Layouts are .cshtml files that define a top-level template for views in the app.  Views reference layouts.  They are not required.
They usually include common UI elements like the header, navigation, menu, and footer.  
They can also include HTML scripts and stylesheets that are used by many pages in the app.

# Razor Directives
The `@` keyword indicates the transition from HTML to C#:  
`@bind` — Binds a C# variable to an HTML object.  
`@code{ … }` — Define a C# code block for complex expressions.  
`@expression()` — A simple C# expression.  
`@inject class-instance` — Injects an instance of Class as Instance into this Component.  
`@model type` — Specifies the type of model passed to the Razor Page  
`@page "/counter"` — Identifies this Component as a Razor Page with a route; it makes the file an MVC action so it can handle requests.  

- Note:  Must be the first directive on the a page.  
  `@variable` — A single C# variable.

# HTML Helpers
```cs
@Html.DisplayNameFor(model => model.Movie[0].Title)
```

Inspects the Title property to determine the display name.

- Note:  The lambda expression is inspected, not evaluated—there is no access violation if the property is null or empty.

# Components
Components make up portions of the app UI.  Each `.razor` file is a component.

## Adding Components to Projects
Visual Studio:  Right-click **Pages** > **Add** > **Razor Component**  
Command Line:  `dotnet new razorcomponent -n Name -o Pages`  

## Parameters
Components can have parameters.  They are specified using attributes:

```cs
@code
{
    private int currentCount = 0;

    [Parameter] // This attribute makes IncrementAmount a parameter of this component.
    public int IncrementAmount { get; set; } = 1;

    private void IncrementCount() => currentCount += IncrementAmount;
}
```

Add a Component to a page with an element:

```html
<Counter />
```

Add a parameter to an element:

```html
<Counter IncrementCount="10" />
```

# Data Binding & Events
Within Razor Components, HTML elements can be bound to C# fields, properties, and Razor expression values.  This allows two-way sync between HTML and .NET.

Data is pushed from HTML to .NET when a Component is rendered.  Components render themselves after event-handler code executes.

# Initialization
```cs
OnInitializedAsync()
// This method fires when a component's initialization is complete but before the page is rendered.

// You can override this method and use it to fetch data:
private Pizza[] todaysPizzas;

protected override async Task OnInitializedAsync()
{
    todaysPizzas = await PizzaSvc.GetPizzasAsync();
}
```

# Layouts

`Pages/Shared/_Layout.cshtml`

# App.razor

The starting point for all Blazor applications:

```html
<!-- The base component for the application.  Contains the program type from Program.cs:  -->
<Router AppAssembly="@typeof(Program).Assembly">
    <!-- The router has 2 options: Found and NotFound  -->
    <!-- If a page is compiled into the application that matches "routeData," it is rendered:  -->
    <Found Context="routeData">
        <!-- Pass the route data (URL parameters), and set the layout.  -->
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <!-- The MainLayout is used, but the page just displays a simple message:  -->
        <LayoutView Layout="@typeof(MainLayout)">
        <p>Sorry, The light has gone out!</p>
        </LayoutView>
    </NotFound>
</Router>
```

# Model Binding
Model binding to properties removes the need to convert HTTP data to the model type.  To opt in to model binding for a property:
```cs
[BindProperty]
public Customer? Customer { get; set; }
```

Razor Pages, by default, only binds properties with non-GET verbs.  You must opt in to binding GET request data to page model properties.  Always verify user input first:
```cs
[BindProperty(SupportsGet = true)]
```