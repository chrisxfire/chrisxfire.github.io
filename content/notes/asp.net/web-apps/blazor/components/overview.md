---
title: overview
date: 2023-05-08T00:00:00-00:00
draft: false
weight: -1
---

# Abstract
A *component* is an element of UI — a page, dialog, button, form, etc — that is built into a .NET assembly.  It includes layout and logic.

Components can be nested, reused, shared among projects, and used in MVC and Razor Pages apps.

# High-level Process for Building Components
1. Create `ComponentName.razor` under `/Pages` (if the Component produces a page) or `/Shared` (otherwise)
2. If the Component requires CSS styling, add it to a code-behind in `ComponentName.razor.css`
3. If the Component will use any services:
    1. Inject the service into the Component:
       ```cs
       @inject ServiceName
       ```

    2. Register the service with DI:
       `Program.cs`
       ```cs
       // use a Scoped lifetime for correct behavior for both Blazor Server and Blazor WebAssembly apps
       builder.Services.AddScoped<ServiceName>(); 
       ```
    3. Add the service to global imports:
       `_Imports.razor`
       ```cs
       @using ServiceName.ClassName
       ```
4. Implement `IDisposable`
   ```cs
   @implements IDisposable
   // ...
   void IDisposable.Dispose()
   {
    // ...
   }
   ```
5. Add the Component to the main layout:  
   `MainLayout.razor`
   ```html
   <ComponentName />
   <!-- ... -->
   ```

# Naming
Component's UI part are in `.razor` files and the logic is in a code-behind `.razor.cs` file.  

Page Components (Components that produce pages) are defined under `/Pages` by convention.  Other Components are defined under `/Shared` or `/Components`.

# Component Namespaces
Components can be placed anywhere in the project.

For an app with a root namespace of `BlazorSample`, the `Pages/Counter.razor` component has a namespace of `BlazorSample.Pages`.

Adding a `@using` directive to parent components or to the app's `_Imports.razor` file.  
`@using` directives in `_Imports.razor` are only applied to `.razor` files, not `.cs` files.

# Lifecycle
Components have lifecycle methods that are called at different points in the Component's lifetime.

## Important Lifecycle Events
- `OnInitialized()` / `Async()` — invoked while Component is initializing
- Use when setting up data that a Component needs 
- `OnParametersSet()` / `Async()` — invoked after OnIntiailize when new values for parameters are received
- `OnAfterRender()` / `Async()` — invoked when Component has finished rendering
- Use this event when needing to interact with JavaScript

## Overriding Lifecycle Events
Example:
```cs
protected override void OnInitialized()
{
}
```

# Markup
In Razor markup, members of the class are defined in `@code` blocks.  These component members are used in rendering logic:
`Pages/Markup.razor`
```html
@page "/markup"

<h1 style="font-style:@headingFontStyle">@headingText</h1>
```
```cs
@code {
    private string headingFontStyle = "italic";
    private string headingText = "Put on your new Blazor!";
}
```

# Routing
Routing in Blazor involves providing a route template to each accessible component in the app with an `@page` directive.
1. When a Razor component is compiled, the generated class receives a `RouteAttribute` that contains its route template.
2. When the app starts, the `Router`'s `AppAssembly` is scanned for all Components that have a `RouteAttribute`.
3. The `RouteView` component receives the `RouteData` from the `Router` and renders the specified Component with its layout.

Components support multiple route templates using multiple `@page` directives:
```html
@page "/blazor-route"
@page "/different-blazor-route"

<h1>Blazor routing</h1>
```

Constant-based route templates can be specified with `@attribute`:
```html
// do not include an @page directive
@attribute [Route(Constants.CounterRoute)]
```

# DynamicComponent
`DynamicComponent` allows Blazor to render components dynamically rather than be specifying their type:

`SomePage.razor`
```html
@foreach (var widgetType in Widgets)
{
    <DynamicComponent Type="widgetType"></DynamicComponent>
}
```

`SomePage.razor.cs`
```cs
public partial class SomePage
{
    public List<Type> Widgets { get; set; } = new() { typeof(SomeWidget), typeof(AnotherWidget) };
}
```

# Differences in Razor Components vs Razor Pages
## No Asynchronous Work in Razor Expressions
Blazor (unlike in Razor Pages) cannot perform asynchronous work in a Razor expression while rendering a component.  This is because Blazor renders interactive UIs; it does not make sense to block while rendering.  

<r>This is illegal</r>:  `<ParameterChild Title="@await ..." />`

Instead, use asynchronous lifecycle events (explained below).

## No Concatenation of Explicit Razor Expression with an Expression Result for Assignment to a Parameter
This is valid in Razor Pages, but not a Razor Component:  

`<ParameterChild Title="Set by @(panelData.Title)" />`

Instead, use a method, field, or property:
```html
<ParameterChild Title="@GetTitle()" />
```
```cs
@code {
	…
	private string GetTitle() => $"Set by {panelData.Title}";
	…
}
```

## No Support for Tag Helpers in Components
Instead, create a Component with the same functionality as the tag helper and use that Component instead.
