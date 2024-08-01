---
title: navigation
date: 2023-07-18T00:00:00-06:00
draft: false
weight: 2
---

# [NavigationManager](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/routing?view=aspnetcore-7.0#uri-and-navigation-state-helpers)
Use `NavigationManager` to manage URIs and navigation in C# code.  `NavigationManager` is added to the DI container by the framework (no registration required).

```cs
[Inject] // injects a NavigationManager instance
public NavigationManager NavMan { get; set; }
NavMan.NavigateTo($"/employeedetail/{selectedEmployee.EmployeeId}");
```

`NavigationManager` uses the browser's history API to maintain navigation history.

## Navigation Options
`NavigateManager`'s `NavigateTo` method accepts `NavigationOptions`:
- `ForceLoad` — bypass client-side routing and force the browser to load the new page from the server; default = `false`
- `ReplaceHistoryEntry` — replace teh current entry in the history stack; default = `true`; if `false`, append instead of replace 
- `HistoryEntryState` — get or set the state to append to the history entry

# Location Changes
`NavigationManager`'s `LocationChanged` event has `LocationChangedEventArgs` that provide information about navigation events including:
- `Location` — the URL of the new location
- `IsNavigationIntercepted` — boolean if Blazor intercepted the navigation from the browser

## Example
```html {hl_lines=[2,3]}
@page "/navigate"
<!-- IDisposable is implemented to unhook the event handler method when Dispose is called by the framework: -->
@implements IDisposable
<!-- NavigationManager is injected: -->
@inject NavigationManager Navigation

<h1>Navigate in component code example</h1>

<button class="btn btn-primary" @onclick="NavigateToCounterComponent">
    Navigate to the Counter component
</button>
```
```cs
@code {
    private void NavigateToCounterComponent()
    {
        Navigation.NavigateTo("counter");
    }

    protected override void OnInitialized()
    {
        // The HandleLocationChanged event handler method is hooked to the LocationChanged event:
        Navigation.LocationChanged += HandleLocationChanged;
    }

    // The event handler method is defined:
    private void HandleLocationChanged(object? sender, LocationChangedEventArgs e)
    {
        // do something
    }

    public void Dispose()
    {
        // When this component is diposed, the event handler method is unhooked from the event:
        Navigation.LocationChanged -= HandleLocationChanged;
    }
}
```

## Handling/Preventing Location Changes with LocationChangingContext
`NavigationManager` has a `RegisterLocationChangingHandler` method that registers a handler to process incoming navigation events. `RegisterLocationChangingHandler`: 
- Accepts as its parameter any method with a `ValueTask` return type and a `LocationChangingContext` parameter
- Returns an `IDisposable` that can be disposed to unregister the location changing handler
 
`LocationChangingContext` has the following properties:
- `TargetLocation` — gets the target location
- `HistoryEntryState` — gets the state associated with the target history entry
- `IsNavigationIntercepted` — boolean whether navigation was intercepted from a link
- `PreventNavigation` — called to prevent navigation from continuing
- `CancellationToken`

Location changing handlers are normally registered in `OnAfterRender{Async}`.  These handlers are on any *internal* navigation event:
- `NavigationMangager.NavigateTo` is called
- Internal links are selected
- The browser's forward and back buttons are used

### Example
```html
@page "/nav-handler"
@inject NavigationManager Navigation
@implements IDisposable

<p>
    <button @onclick="@(() => Navigation.NavigateTo("/"))">
        Home (Allowed)
    </button>
    <button @onclick="@(() => Navigation.NavigateTo("/counter"))">
        Counter (Prevented)
    </button>
</p>
```
```cs
@code {
    // This IDisposable will be assigned the IDisposable that's returned from RegisterLocationChangingHandler()
    private IDisposable? registration;

    protected override void OnAfterRender(bool firstRender)
    {
        if (firstRender)
        {
            // Now set to RegisterLocationChangingHandler's IDisposable
            registration = Navigation.RegisterLocationChangingHandler(OnLocationChanging);
        }
    }

    // Note that this method must return a ValueTask and have a LocationChangingContext parameter:
    private ValueTask OnLocationChanging(LocationChangingContext context)
    {
        if (context.TargetLocation == "/counter")
        {
            // LocationChangingContext's PreventNavigation method is used:
            context.PreventNavigation();
        }

        return ValueTask.CompletedTask;
    }

    // The LocationChangingHandler is disposed:
    public void Dispose() => registration?.Dispose();
}
```

## Handling/Preventing Location Changes with NavigationLock
The `NavigationLock` component can intercept navigation events as long as it has rendered.  It "locks" any navigation until a decision is made to proceed or cancel.
`NavigationLock` should be used when navigation can be scoped to the lifetime of the component.

NavigationLock has two parameters:
- `ConfirmExternalNavigation` — boolean if a browser dialog should prompt the user to confirm or cancel navigation; default = `false`
- `OnBeforeInternalNavigation` — accepts a LocationChangingContext for internal navigation events

### Example
`Pages/NavLock.razor`
```html
@page "/nav-lock"
@inject IJSRuntime JSRuntime
@inject NavigationManager Navigation

<NavigationLock ConfirmExternalNavigation="true" 
    OnBeforeInternalNavigation="OnBeforeInternalNavigation" />

<p>
    <button @onclick="Navigate">Navigate</button>
</p>

<p>
    <a href="https://www.microsoft.com">Microsoft homepage</a>
</p>
```
```cs
@code {
    private void Navigate()
    {
        Navigation.NavigateTo("/");
    }

    private async Task OnBeforeInternalNavigation(LocationChangingContext context)
    {
        var isConfirmed = await JSRuntime.InvokeAsync<bool>("confirm", 
            "Are you sure you want to navigate to the Index page?");

        if (!isConfirmed)
        {
            context.PreventNavigation();
        }
    }
}
```
