---
title: js interop
date: 2023-01-01T00:00:00-07:00
draft: false
weight: 1
---

# Overview
- .NET can invoke JavaScript and vice-versa.  
- `IJSRuntime` is automatically registered as a service by the Blazor framework.
- Documentation: 
  - https://learn.microsoft.com/en-us/aspnet/core/blazor/javascript-interoperability/?view=aspnetcore-7.0
  - https://learn.microsoft.com/en-us/aspnet/core/blazor/javascript-interoperability/call-javascript-from-dotnet?view=aspnetcore-7.0

<r>Warning</r>: JavaScript code must only be executed **after** the Component is fully rendered.  Invoke JavaScript from the `OnAfterRenderAsync` method.

## Prerendering
Invoking JavaScript <o>is not possible during prerendering.</o>

# JavaScript Locations
## In `<body>` markup
Place the JavaScript inside the closing `</body>` element of `wwwroot/index.html` (Blazor WASM) or `Pages/_Host.cshtml` (Blazor Server): 
```html
<body>
    ...

    <script src="_framework/blazor.{server|webassembly}.js"></script>
    <script>
      <!-- JavaScript starts here: -->
      window.jsMethod = (methodParameter) => {
        ...
      };
    </script>
</body>
```

## From a JavaScript File
Place the JavaScript `src` reference inside the closing `</body>` element of `wwwroot/index.html` (Blazor WASM) or `Pages/_Host.cshtml` (Blazor Server): 

```html
<body>
    <!-- ... -->
    <script src="_framework/blazor.{server|webassembly}.js"></script>
    <script src="{SCRIPT PATH AND FILE NAME (.js)}"></script>
</body>
```

## JavaScript Code-Behind
For a Blazor component `SomeComponent` in `Pages/SomeComponent.razor`, place the JavaScript code-behind for that component in `Pages/SomeComponent.razor.js`:

`Pages/SomeComponent.razor`
```html
<!-- ... -->
```
```cs
@code {
    // ...
    private IJSInProcessObjectReference? module;

    protected override void OnAfterRenderAsync() {
        module = await JS.InvokeAsync<IJSObjectReference>("import", "./Pages/SomeComponent.razor.js");
    }

    // ...

    async ValueTask IAsyncDisposable.DisposeAsync()
    {
        if (module is not null)
            await module.DisposeAsync();
    }
}
```

`Pages/SomeComponent.razor.js`
```js
export function showPrompt(message) {
  return prompt(message, 'Type anything here');
}
```

## Injecting a Script Before/After Blazor Starts
See [JavaScript initializers](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/startup?view=aspnetcore-7.0#javascript-initializers).

## JavaScript Isolation
See [JavaScript isolation in JavaScript modules](https://learn.microsoft.com/en-us/aspnet/core/blazor/javascript-interoperability/call-javascript-from-dotnet?view=aspnetcore-7.0#javascript-isolation-in-javascript-modules).

# Invoking JavaScript from .NET
## 1. Add the script to `wwwroot` or as an inline script with `<script>` tag
## 2. Register the script in the hosting page (`index.html` or `host.cshtml`)
```html
<script>
window.DoSomething = () => {
    // do something here
}
</script>
```

## 3. Inject `IJSRuntime` via DI
```cs
@code 
{
    [Inject]
    public IJSRuntime JsRuntime { get; set; }
}
```

## 4. Call the script (invoke the JavaScript function) from .NET
```cs
protected async override Task OnAfterRenderAsync(bool firstRender) 
{
    // if expecting a value to be returned:
    var result = await JsRuntime.InvokeAsync<object>("DoSomething", "");
    // else...
    _ = await JsRuntime.InvokeVoidAsync<object>("DoSomething", "");
}
``` 

## InvokeAsync vs InvokeVoidAsync
Use `InvokeVoidAsync` when .NET is not required to read the result of a JavaScript call, or the JavaScript function being called returns `void` or `undefined`.

# JavaScript Interop Call Timeouts
By default, Blazor Server apps use a timeout of 60 seconds for interop calls.

## Change the Global Timeout
`Program.cs`
```cs
builder.Services.AddServerSideBlazor(
    options => options.JSInteropDefaultCallTimeout = TimeSpan.FromSeconds(30));
```

## Change the Timeout per Call
```cs
// {ID} is the placeholder for the identifier of the JavaScript function to invoke:
var result = await JS.InvokeAsync<string>("{ID}", TimeSpan.FromSeconds(30), new[] { "Arg1" });
```

# Catch JavaScript Exceptions
Wrap the interop call in a try/catch block and catch `JSException`:
```cs
try
{
    var result = await JS.InvokeAsync<string>("nonFunction");
}
catch (JSException e)
{
    var errorMessage = $"Error Message: {e.Message}";
}
```

# Render UI with JavaScript
See [JavaScript Libraries that render UI](https://learn.microsoft.com/en-us/aspnet/core/blazor/javascript-interoperability/call-javascript-from-dotnet?view=aspnetcore-7.0#javascript-libraries-that-render-ui).

# Abort Long-Running JavaScript
See [Abort a long-running JavaScript function](https://learn.microsoft.com/en-us/aspnet/core/blazor/javascript-interoperability/call-javascript-from-dotnet?view=aspnetcore-7.0#abort-a-long-running-javascript-function).
