---
title: events
date: 2023-05-06T00:00:00-06:00
draft: false
weight: 1
---

# overview
[HTML events](https://www.w3schools.com/tags/ref_eventattributes.asp), like `onclick`, can be handled in Blazor. To specify an event callback, use an attribute that starts with `@on` and ends with the event name. The value of the attribute (`IncrementCount`) is the name of the C# method (event handler) to call:
```html
<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>
```

Event handlers can also be defined inline using C# lambda expressions:
```html
<button class="btn btn-primary" @onclick="() => currentCount++">Click me</button>
```

Event handler methods can optionally take an event argument with information about the event:
```html
<input @onchange="InputChanged" />
<p>@message</p>
```
```cs
@code {
    string message = "";

    void InputChanged(ChangeEventArgs e)
    {
        message = (string)e.Value;
    }
}
```

## default event arguments
Some events support event arguments.  For example:
- `@onclick` passes `MouseEventArgs`
- `@onkeydown` passes `KeyboardEventArgs`

Example
```html
<button @onclick="ShowLocation">Show</button>
```
```cs
@code 
{
    private void ShowLocation(MouseEventArgs e)
    {
    }
}
```
## `EventCallback`
When an event occurs in a child Component, use `EventCallback` to trigger code to execute in the parent Component:

`ChildComponent.razor`
```html
<button @onclick="TriggerCallbackToParent">Show</button>
```
```cs
@code
{
    [Parameter]
    public EventCallback<MouseEventArgs> TriggerCallbackToParent { get; set; }
}
```
`ParentComponent.razor`
```html
<ChildComponent TriggerCallbackToParent="ShowPopup"></ChildComponent>
```
```cs
@code
{
    private void ShowPopup()
    {
        …
    }
}
```

