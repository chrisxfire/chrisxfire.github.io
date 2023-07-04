---
title: notes > code > asp.net > web apps > blazor > fundamentals > logging
date: 2023-04-18T00:00:00-06:00
draft: false
---

# Logging in Components
Inject an `ILogger`:  
`Pages/Counter1.razor`
```html
@page "/counter-1"
@inject ILogger<Counter> logger

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>
```
```cs
@code {
    private int currentCount = 0;

    private void IncrementCount()
    {
        logger.LogWarning("Someone has clicked me!");

        currentCount++;
    }
}
```
