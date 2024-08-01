---
title: overview
date: 2023-01-11T00:00:00-06:00
draft: false
weight: -1
---

# [Overview](https://learn.microsoft.com/en-us/aspnet/core/blazor/?view=aspnetcore-7.0)
Blazor is a server-side rendered (Server) or client-side rendered (WASM) framework for web apps.
Blazor does not use a request/response model.

Advantages:
- Create UIs in combination of HTML and C# instead of JavaScript
- Share server-side and client-side app logic
- Render UI as HTML and CSS
- Integrate with Docker
- Build hybrid desktop & mobile apps

Blazor apps are based on Razor components—an element of UI (like a page, dialog, or form).

Components:
- are C# classes
- render UI, handle user events
- written as a .razor file (Razor components; informally, Blazor components)
- NOT built around request/response model (like Razor Pages & MVC)

`Pages/Dialog.razor`
```html
<div class="card" style="width:22rem">
    <div class="card-body">
        <h3 class="card-title">@Title</h3>
        <p class="card-text">@ChildContent</p>
        <button @onclick="OnYes">Yes!</button>
    </div>
</div>
```
```cs
@code {
    [Parameter]
    public RenderFragment? ChildContent { get; set; } // text of the dialog

    [Parameter]
    public string? Title { get; set; } // title of the dialog

    private void OnYes() // triggered by the button's onclick event
    {
   // write's to the browser's console
        Console.WriteLine("Write to the console in C#! 'Yes' button selected.");
    }
}
```

`Pages/Index.razor`
```html
@page "/"

<h1>Hello, world!</h1>

<p>
    Welcome to your new app.
</p>

<Dialog Title="Learn More"> <!-- uses the previously-defined Dialog component --> 
    Do you want to <i>learn more</i> about Blazor? <!-- sets the Dialog component's ChildContent (text) -->
</Dialog>
```

# Tooling
## Visual Studio / dotnet new templates
- Blazor Server App (`blazorserver`) template — includes demonstration code and Bootstrap
- Blazor Server App Empty (`blazorserver-empty`) template — no demo code, no Bootstrap
- Blazor WASM (`blazorwasm`) template — includes demonstration code and Bootstrap
- Blazor WASM Empty (`blazorwasm-empty`) template — no demo  code, no Bootstrap
- ASP.NET Core Hosted checkbox — check for a hosted Blazor WASM app
    - The startup project is in the Server project

## .NET WebAssembly build tools
Based on Emscripten, a compiler toolchain for the web platform.  To install, either:
- Visual Studio installer > **Additional Components** > **.NET WebAssembly build tools**
- `dotnet workload install wasm-tools`
Note:  .NET 7 build tools (installed above) are incompatible with .NET 6.  To use the .NET 6 build tools:  
`dotnet workload install wasm-tools-net6`

When AOT compilation is used, SIMD is supported except for Apple Safari.  To enable this:
```xml
<PropertyGroup>
  <WasmEnableSIMD>true</WasmEnableSIMD>
  <RunAOTCompilation>true</RunAOTCompilation>
</PropertyGroup>
```
To enable WASM exception handling:
```xml
<PropertyGroup>
  <WasmEnableExceptionHandling>true</WasmEnableExceptionHandling>
</PropertyGroup>
```
