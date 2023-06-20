---
title: notes > asp.net > web apps > blazor > components > classes and nesting
date: 2023-04-01T00:00:00-06:00
draft: false
---

# Component Classes
`ComponentBase` is the base class for Razor components.  It implements `IComponent.`

Components are generated as C# partial classes.  They can either be written as:  
1. A single file with C# `@code` blocks, HTML markup, and Razor markup, like:  

`Pages/Counter.razor`
```html
@page "/counter"

<PageTitle>Counter</PageTitle>

<h1>Counter</h1>

<p role="status">Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        currentCount++;
    }
}
```
2. Or, HTML and Razor markup in a `.razor` file and C# code in a `.cs` code-behind file, like:  

`Pages/Counter.razor`
```html
@page "/counter-partial-class"

<PageTitle>Counter</PageTitle>

<h1>Counter</h1>

<p role="status">Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>
```
`Pages/Counter.razor.cs`
```cs
namespace BlazorSample.Pages;

// The class MUST be partial:
public partial class CounterPartialClass
{
    private int currentCount = 0;

    private void IncrementCount()
    {
        currentCount++;
    }
}
```
# Base Classes
Use `@inherits`:  
`Pages/BlazorRocks.razor`
```html
@page "/blazor-rocks"
@inherits BlazorRocksBase @*specifies BlazorRocksBase.cs as a base class*@

<h1>@BlazorRocksText</h1> @*this string is defined in the base class*@
```

# Nested Components
Components can include other components by declaring them in HTML.

This `Heading` component…  
`Shared/Heading.razor`
```html
@* If @page "/heading" were included here, this component would be accessible at /heading and /heading-example. *@
<h1 style="font-style:@headingFontStyle">Heading Example</h1>

@code {
    private string headingFontStyle = "italic";
}
```
…can be used in this example as an HTML tag:  
`Pages/HeadingExample.razor`
```html
@page "/heading-example"

<Heading />
```
