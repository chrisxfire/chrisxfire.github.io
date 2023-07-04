---
title: notes > code > asp.net > web apps > blazor > components > events
date: 2023-05-06T00:00:00-06:00
draft: false
---

# Overview
DOM events can be assigned an event handler to execute code when the event is triggered:  
`@onsomeDOMevent="Delegate"`
	
Example
```html
<button @onclick="SaveEmployee">Save</button>
```
```cs
@code 
{
    private void SaveEmployee()
    {
        …
    }
}
```
# Default Event Arguments
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
# `EventCallback`
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
