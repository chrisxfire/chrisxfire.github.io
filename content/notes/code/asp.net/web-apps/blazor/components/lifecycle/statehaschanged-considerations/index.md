---
title: notes > code > asp.net > web apps > blazor > components > lifecycle > statehaschanged considerations
date: 2023-07-02T00:00:00-06:00
draft: false
---

# Overview
`StateHasChanged()` is called to notify the Component that its state has changed.  When applicable, calling this method can cause the Component to be rerendered. 
This is necessary when the Component updates due to an external change (like an event from a service). In these cases, the Component does not update automatically.

`StateHasChanged()` is called automatically for `EventCallback` methods.

# Problem
> Credit: [Blazor University](https://blazor-university.com/components/multi-threaded-rendering/invokeasync/)

When code is called by a non-UI event, a thread locking/synchronization mechanism is normally required if we intend to manipulate state.  Non-UI events include:
- A callback from a `System.Threading.Timer`
- An event tirggered by another thread on a Singleton instance shared by multiple users
- A data push from another server we've connected to via a Web Socket

In WPF apps, `Dispatcher.Invoke` ensures the UI thread executes the code. In WinForms, the `Invoke` method of the form is used. This avoids the need to thread synchronizing code.

In Blazor Server, there is a single dispatched associated with each connection (browser tab). The `StateHasChanged()` framework method throws an exception if a secondary thread accesses the rendering process at the same time. 

> Blazor WASM apps are single-threaded and so thread safety is not a concern.

# Solution: `InvokeAsync()` 
When calling `StateHasChanged()` from one of the above scenarios, invoke it via the `InvokeAsync()` method. `InvokeAsync()` serializes the work.

## Example
Wrap the call to `StateHasChanged` in `InvokeAsync()`:  
```cs
InvokeAsync(StateHasChanged);
```