---
title: routing
date: 2023-04-17T00:00:00-06:00
draft: false
weight: -1
---

# overview
- Documentation: https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/routing?view=aspnetcore-7.0

# router component
(In this section, `Navigation` is an injected `NavigationManager`)  
The `Router` component enables routing:

`App.razor`
```html
<Router AppAssembly="@typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <p>Sorry, there's nothing at this address.</p>
    </NotFound>
</Router>
```

## focus
Set the UI focus to an element based on a CSS selector.  When the `Router` navigates to a new page, this sets the focus to the page's top-level header:
```html
<FocusOnNavigate RouteData="@routeData" Selector="h1" />
```

## provide custom content when content not found
Use the `NotFound` template:  
`App.razor`
```html
<Router AppAssembly="@typeof(Program).Assembly">
    <Found Context="routeData">
        <RouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)" />
    </Found>
    <NotFound>
        <p>Sorry, there's nothing at this address.</p>
    </NotFound>
</Router>
```

## tell router to search additional assemblies for components
Use the `AdditionalAssemblies` parameter:
```html
<Router
    AppAssembly="@typeof(App).Assembly"
    AdditionalAssemblies="new[] { typeof(Component1).Assembly }">
    @* ... Router component elements ... *@
</Router>
```

## routing urls with dots
For hosted Blazor WASM and Blazor Server apps
- The default route template assumes that, if the last segment of a request URL contains a dot, a file is requested.
- Example:  if the request URL is `/example/some.thing` the `Router` interprets this to be a request for the file `some.thing`.

If `some.thing` is a route parameter value, the app must be configured with a custom route template.
- For Blazor WASM's Server project, in `Program.cs`:
    ```cs
    app.MapFallbackToFile("/example/{param?}", "index.html");
    ```
- For Blazor Server, in `Program.cs`:
    ```cs
    app.MapFallbackToPage("/example/{param?}", "/_Host");
    ```

## handling asynchronous navigation events
`Router` has an `OnNavigateAsync` handler.  It is passed a `NavigationContext`.  It is invoked when:
1. A user visits a route for the first time by navigating to it directly in their browser
2. A user navigates to a new route using a link or the `NavigationManager.NavigateTo` invocation

`App.razor`
```html
<Router AppAssembly="@typeof(App).Assembly" 
    OnNavigateAsync="@OnNavigateAsync">
    ...
</Router>
```
```cs
@code {
    private async Task OnNavigateAsync(NavigationContext context)
    {
        // ...
    }
}
```  

<o>Note</o>:  In Blazor Server and hosted Blazor WASM apps, when prerendering, `OnNavigateAsync` is executed twice: one when the endpoint component is initially rendered (statically), and again when the browser renders the endpoint component.  
- `App.razor` can store the `NavigationContext` for use in `OnAfterRender{Async}`, which has a `bool firstRender` that can be checked.

### handling cancellations
The `NavigationContext` passed to `OnNavigateAsync` contains a `CancellationToken` property.  This `CancellationToken` is set whenever a new navigation event occurs.  When implementing `OnNavigateAsync`, the callback <o>must</o> throw if cancellation is requested to avoid unintended behavior.

# `<Navigating>` Content
The `Router` can indicate to the user that a page transition is occurring:
`App.razor`
```html
@using Microsoft.AspNetCore.Components.Routing

<Router>
    <!-- ... -->
    <Navigating>
        <p>Loading the requested page&hellip;</p>
    </Navigating>
    <!-- ... -->
</Router>
```

# [NavLink and NavMenu Components](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/routing?view=aspnetcore-7.0#navlink-and-navmenu-components)
[See notes in Components.](../../../components/navlink-and-navmenu-components)
