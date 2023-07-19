---
title: notes > asp.net > web apps > blazor > components > lifecycle > overview
date: 2023-05-26T00:00:00-06:00
draft: false
weight: -1
---

# Overview
Component lifecycle events are processed in a set of lifecycle methods.  These methods can be overridden to perform additional operations in Components during Component initialization and rendering.

## General lifecycle
1. If the Component is rendered for the first time on a request:
   1. Create the Component's instance
   2. Perform property injection.  Run `SetParametersAsync`.
   3. Call `OnInitialized{Async}`.
2. Call `OnParametersSet{Async}`.
3. Render.

<img src="lifecycle1.png" width="50%" height="50%">

# SetParametersAsync()
`SetParametersAsync()` sets parameters supplied by the Component's parent. It contains a `ParameterView` parameter that contains the component parameter values for the Component. This method can be overridden to interact directly with `ParameterView`'s parameters.

More: https://learn.microsoft.com/en-us/aspnet/core/blazor/components/lifecycle?view=aspnetcore-7.0#when-parameters-are-set-setparametersasync

# OnInitialized{Async}()
`OnInitialized{Async}()` is invoked when the Component is initialized after having received its initial parameters in SetParametersAsync.

## Prerendering consideration
Blazor apps that prerender their content on the server call `OnInitializedAsync` *twice*:
* Once when Component is initially rendered statically
* A second time when the browser renders the Component

# OnParametersSet{Async}()
`OnParametersSet{Async}()` is invoked:
* After the Component is initialized
* When the parent Component renders and supplies:
  * Immutable types and at least one parameter has changed
  * Complex-typed parameters

# OnAfterRender{Async}()
`OnAfterRender{Async}()` is invoked after a Component has finished rendering.  JS interop calls should happen at this stage.

`OnAfterRender{Async}()` contains a `firstRender` parameter that is set to `true` the first time the Component instance is rendered:
```cs
protected override void OnAfterRender(bool firstRender)
{
    if (firstRender) 
    {
        //...
    }
}
```

## Prerendering consideration
`OnAfterRender{Async}()` is *not* called during the prerendering process on the server.

# StateHasChanged()
`StateHasChanged()` is called to notify the Component that its state has changed.  When applicable, calling this method can cause the Component to be rerendered. 
This is necessary when the Component updates due to an external change (like an event from a service). In these cases, the Component does not update automatically.

`StateHasChanged()` is called automatically for `EventCallback` methods.

<o>StateHasChanged has some important considerations</o>. See [here](../statehaschanged-considerations/).

# Handle Incomplete Async Actions at Render
Async actions performed in lifecycle events may not have completed before the Component is rendered.  Provide rendering logic to confirm that objects are initialized.  Render placeholder UI elements (like a "loading" message) while the objects are null.

See the `FetchData` component in the Blazor default template for an example.

# Stateful Reconnection After Prerendering
See: https://learn.microsoft.com/en-us/aspnet/core/blazor/components/lifecycle?view=aspnetcore-7.0#stateful-reconnection-after-prerendering

# Prerendering with JavaScript Interop
See: https://learn.microsoft.com/en-us/aspnet/core/blazor/components/lifecycle?view=aspnetcore-7.0#prerendering-with-javascript-interop

# Component Disposal
See: https://learn.microsoft.com/en-us/aspnet/core/blazor/components/lifecycle?view=aspnetcore-7.0#component-disposal-with-idisposable-and-iasyncdisposable

# Cancelable Background Work
See: https://learn.microsoft.com/en-us/aspnet/core/blazor/components/lifecycle?view=aspnetcore-7.0#cancelable-background-work
