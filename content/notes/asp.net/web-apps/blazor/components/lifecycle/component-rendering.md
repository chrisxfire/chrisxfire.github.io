---
title: notes > asp.net > web apps > blazor > components > lifecycle > component rendering
date: 2023-07-26T00:00:00-06:00
draft: true
weight: 1
---

# Overview
- Components *must* render when they are first added to the component hierarchy by a parent component.
- Components *may* render at other times according to their own logic and conventions.
- Documentation: https://learn.microsoft.com/en-us/aspnet/core/blazor/components/rendering?view=aspnetcore-7.0

# Rendering Flow
In most cases, `ComponentBase` conventions result in the correct subset of component rerenders after an event occurs.  Developers are not required to provide manual logic to tell the framework which components to rerender and when to rerender them.

# Managing UI Refreshes (When to Override ShouldRender)
The `ShouldRender` method is called each time a component is rendered.  Override `ShouldRender` to manage UI refreshes:  
`Pages/ControlRender.razor`
```html
@page "/control-render"

<label>
    <input type="checkbox" @bind="shouldRender" />
    Should Render?
</label>

<p>Current count: @currentCount</p>

<p>
    <button @onclick="IncrementCount">Click me</button>
</p>
```
```cs
@code {
    private int currentCount = 0;
    private bool shouldRender = true;

    protected override bool ShouldRender()
    {
        return shouldRender;
    }

    private void IncrementCount()
    {
        currentCount++;
    }
}
```

# When to Call StateHasChanged
Calling `StateHasChanged` allows you to trigger a render at any time.

You need not call `StateHasChanged` when:
- Routinely handling events (`ComponentBase` triggers a render for most routine event handlers)
- Implementing [typical lifecycle logic](./overview/index.md) in lifecycle methods (`ComponentBase` triggers a render for typical lifecycle events) 

You *may* need to call `StateHasChanged` in the following scenarios:

## An asynchronous handler invokes multiple asynchronous phases
A receiver of a `Task` can only observe its final completion, not intermediate asynchronous states.  Therefore, `ComponentBase` only triggers rerender when the Task is first returned and when the Task finally completes.  To rerender at intermediate points, call `StateHasChanged`.

### Example
In this code, CounterState1 updates the count four times on each click:
- Automatic rerenders occur after the first and last increments of `currentCount`.
- Manual renders are used in intermediate points.
`Pages/CounterState1.razor`
```html
@page "/counter-state-1"

<p>
    Current count: @currentCount
</p>

<p>
    <button class="btn btn-primary" @onclick="IncrementCount">Click me</button>
</p>
```
```cs
@code {
    private int currentCount = 0;

    private async Task IncrementCount()
    {
        currentCount++;
        // Renders here automatically

        await Task.Delay(1000);
        currentCount++;
        StateHasChanged();

        await Task.Delay(1000);
        currentCount++;
        StateHasChanged();

        await Task.Delay(1000);
        currentCount++;
        // Renders here automatically
    }
}
```

## Receiving a call from something external to the Blazor rendering and event handling system
`ComponentBase` only knows about its own lifecycle methods and Blazor-triggered events, not other events that may occur.  To trigger rerender with these events, call `StateHasChanged`.

## To render a component outside the subtree that's rerendered by a particular event
Consider a UI that:
1. Dispatches an event to one component
2. Changing some state
3. Rrerendering a different component that is not a descendant of the component receiving the event

In such a scenario, *state management* is used.  When one component calls a method on the state manager, the state manager raises an event that is received by an independent component.  Call `StateHasChanged` on other components you wish to rerender in response to the state manager's events.