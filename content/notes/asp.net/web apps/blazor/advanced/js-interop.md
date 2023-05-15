---
title: "notes > asp.net > blazor > advanced > js-interop"
date: 2023-01-01T00:00:00-07:00
draft: false
---

<style>
    r { color: red }
    o { color: orange }
    g { color: green }
</style>

# Overview
.NET can invoke JavaScript and vice-versa.

<!-- TODO: WARNING -->
<r>JavaScript code must only be executed **after** the Component is fully rendered.</r>  Invoke JavaScript from the `OnAfterRenderAsync` method.

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