---
title: route parameters and templates
date: 2023-07-18T00:00:00-06:00
draft: false
weight: 1
---

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
<!-- do not include an @page directive -->
@attribute [Route(Constants.CounterRoute)]
```

# route parameters
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

# constraining route parameters
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

# query strings
To obtain parameter values from a query string:
```cs
[Parameter]
// If the parameter name is the same as the property name, the Name argument is not needed
[SupplyParameterFromQuery(Name = "id")]
public string EmployeeId { get; set; }
```

More: https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/routing?view=aspnetcore-7.0#query-strings
