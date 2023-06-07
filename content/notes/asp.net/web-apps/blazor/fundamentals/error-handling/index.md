---
title: notes > asp.net > web apps > blazor > fundamentals > error handling
date: 2023-04-18T00:00:00-06:00
draft: false
---

# `ErrorBoundary`
Blazor apps do not have a middleware processing pipeline that can be handled for global error handling.  Instead, use the `ErrorBoundary` component.  

The `ErrorBoundary` component renders its child content normally, and renders error UI when an unhandled exception occurs.

Example: wrapping the body content of the app's main layout in `Shared/MainLayout.razor`:
```html
<main>
    <article class="content px-4">
        <ErrorBoundary>
            @Body
        </ErrorBoundary>
    </article>
</main>
```

# `CascadingValue`
As an alternative to `ErrorBoundary`, use an error processing component as a cascading value to handle errors in a centralized way.  A cascaded component can render content and apply CSS styles when an error occurs.

An example error component:  
`Shared/Error.razor`
```html
@using Microsoft.Extensions.Logging
@inject ILogger<Error> Logger

<CascadingValue Value="this">
    @ChildContent
</CascadingValue>
```
```cs
@code {
    [Parameter]
    public RenderFragment? ChildContent { get; set; }

    public void ProcessError(Exception ex)
    {
        Logger.LogError("Error:ProcessError - Type: {Type} Message: {Message}", 
            ex.GetType(), ex.Message);
    }
}
```
In `App.razor`, wrap the `Router` component with `Error`:
```html
<Error>
    <Router ...>
        ...
    </Router>
</Error>
```
To process errors in a component:
```cs
@code {
    private int currentCount = 0;

    // designate the Error component as a CascadingParameter in a @code block:
    [CascadingParameter]
    public Error? Error { get; set; }

    private void IncrementCount()
    {
        try
        {
            currentCount++;

            if (currentCount > 5)
            {
                throw new InvalidOperationException("Current count is over five!");
            }
        }
        catch (Exception ex)
        {
            // call an error processing method in a catch block:
            Error?.ProcessError(ex);
            // if ProcessError renders as well, then call StateHasChanged at the end of the method to render the UI
        }
    }
}
```
# [Logging Errors](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/handle-errors?view=aspnetcore-7.0#log-errors-with-a-persistent-provider)
TODO...
