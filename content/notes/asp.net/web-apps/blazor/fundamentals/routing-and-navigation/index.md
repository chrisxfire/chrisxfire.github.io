---
title: notes > asp.net > web apps > blazor > fundamentals > routing and navigation
date: 2023-04-17T00:00:00-06:00
draft: false
---

# Enable Routing
(In this section, `Navigation` is an injected `NavigationManager`)  
Router component enables routing:

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
# Route Templates — How it Works in Blazor
1. When a Razor Component is compiled, the generated class receives a `RouteAttribute` that contains its route template.
2. When the app starts, the `Router`'s `AppAssembly` is scanned for all Components that have a `RouteAttribute.`
3. The `RouteView` Component receives the `RouteData` from the Router and renders the specified component with its layout.

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

# Focus
Set the UI focus to an element based on a CSS selector.  When the `Router` navigates to a new page, this sets the focus to the page's top-level header:
```html
<FocusOnNavigate RouteData="@routeData" Selector="h1" />
```

## Provide Custom Content when Content Not Found
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
# Tell Router to Search Additional Assemblies for Components
Use the `AdditionalAssemblies` parameter:
```html
<Router
    AppAssembly="@typeof(App).Assembly"
    AdditionalAssemblies="new[] { typeof(Component1).Assembly }">
    @* ... Router component elements ... *@
</Router>
```

# Route Parameters
The text segment (case-insensitive) assigns the value of the route segment to the component's `Text` property (which is a Parameter), if it exists:
```html
@page "/route-parameter-2/{text?}"

<h1>Blazor is @Text!</h1>
```
```cs
@code {
    [Parameter]
    public string? Text { get; set; }

    protected override void OnInitialized()
    {
        Text = Text ?? "fantastic";
    }
}
```
If the user should be able to navigate from `/route-parameter-2` to `/route-parameter-2/amazing` or vice versa, use `OnParametersSet` instead of `OnInitialized{Async}`:
```cs
protected override void OnParametersSet()
{
    Text = Text ?? "fantastic";
}
```

## Constraining Route Parameters
Route constraints enforce type matching on a route segment to a component:  
`Pages/User.razor`
```html
@page "/user/{Id:int}/{Option:bool?}" @* The Id route segment must be present in the requesting URL and it must be an int *@

<p>
    Id: @Id
</p>

<p>
    Option: @Option
</p>
```
```cs
@code {
    [Parameter]
    public int Id { get; set; }

    [Parameter]
    public bool Option { get; set; }
}
```
Valid constraints are `bool`, `datetime`, `decimal`, `double`, `float`, `guid`, `int`, and `long.`

# Routing URLs with Dots
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

# Catch-all Route Parameters
To capture paths across multiple folder boundaries, use a catch-all route parameter:  
`Pages/CatchAll.razor`
```html
@page "/catch-all/{*pageRoute}" @* must be at the end of the URL *@
```
```cs
@code {
    [Parameter]
    public string? PageRoute { get; set; }
}
```
For URL `/catch-all/this/is/a/test`, the above route template sets the value of `PageRoute` to `this/is/a/test`.

# [URI and Navigation State Helpers](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/routing?view=aspnetcore-7.0#uri-and-navigation-state-helpers)
Use `NavigationManager` to manage URIs and navigation in C# code.  `NavigationManager` is added to the DI container by the framework (no registration required).
```cs
[Inject] // injects a NavigationManager instance
public NavigationManager NavMan { get; set; }
NavMan.NavigateTo($"/employeedetail/{selectedEmployee.EmployeeId}");
```

## [Location Changes](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/routing?view=aspnetcore-7.0#location-changes)
`LocationChangedEventArgs` provides information about navigation events.

## [Navigation History](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/routing?view=aspnetcore-7.0#navigation-history-state)

## [Query Strings](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/routing?view=aspnetcore-7.0#query-strings)
To obtain parameter values from a query string:
```cs
[Parameter]
// If the parameter name is the same as the property name, the Name argument is not needed
[SupplyParameterFromQuery(Name = "id")]
public string EmployeeId { get; set; }
```

# [`<Navigating>` Content](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/routing?view=aspnetcore-7.0#user-interaction-with-navigating-content)
The `Router` can indicate to the user that a page transition is occurring.

# [Asynchronous Navigation Events](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/routing?view=aspnetcore-7.0#handle-asynchronous-navigation-events-with-onnavigateasync)

# [Handle or Prevent Location Changes](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/routing?view=aspnetcore-7.0#handleprevent-location-changes)

# [NavLink and NavMenu Components](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/routing?view=aspnetcore-7.0#navlink-and-navmenu-components)
