---
title: overview
date: 2023-01-11T00:00:00-06:00
draft: false
weight: -1
tags:
 - kb/asp.net/blazor
---

# [overview](https://learn.microsoft.com/en-us/aspnet/core/blazor/?view=aspnetcore-7.0)
Blazor is a server-side rendered (Server) or client-side rendered (WASM) framework for web apps.  
Blazor does not use a request/response model.

Advantages:
- Create UIs in combination of HTML and C# instead of JavaScript
- Share server-side and client-side app logic
- Render UI as HTML and CSS
- Integrate with Docker
- Build hybrid desktop & mobile apps

## components
Blazor apps are built with Razor *components*, an element of UI (like a page, dialog, or form). When a Razor component in used in a Blazor app, it is informally referred to as a *Blazor component*. Components handle both rendering and UI event handling. There are built-in components, and components can be developed.

Razor files use a mix of HTML, CSS and C#. They are then compiled into C# classes. 

Interactive Blazor components handle standard web UI interactions using C# event handlers. They can update their state in response to UI events, and adjust their rendering.

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

## content rendering
As of .NET 8, Blazor can render content at either the component or page level with:
- Static server rendering (SSR) — to generate static HTML on the server.
- Interactive server rendering (interactive SSR) — to generate interactive components with pre-rendering on the server.
- Interactive WebAssembly rendering aka client-side rendering (CSR) — always interactive; to generate interactive components on the client with pre-rendering on the server.
- Interactive automatic rendering (auto) to initially use the server-side ASP.NET Core runtime for content rendering and interactivity, then the .NET WebAssembly runtime on the client for subsequent rendering and interactivity after the Blazor bundle is downloaded and the WASM runtime activates.

More information: [Rendering](fundamentals/rendering.md)

### rendering C# expression values
To render the value of a C# expression in Razor, use the `@` prefix, like the `currentCount` field here:
```html
<p role="status">Current count: @currentCount</p>
```

To be explicit about when the C# expression ends and HTML resumes, use parentheses:
```html
<p role="status">Current count: @(currentCount)</p>
```

## tooling
### vs code
#### creating a project
1. <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> -> **.NET New Project**
2. Select the Blazor project template
3. Follow the prompts

#### running the app
1. <kbd>F5</kbd> to run with debugger  
2. Select the **C#** debugger from the list
3. Select the **https** launch configuration

To stop, <kbd>Shift</kbd> + <kbd>F5</kbd>

### .NET cli
#### creating a project
- Blazor Web App (`dotnet new blazor`)
- Blazor WebAssembly standalone (`dotnet new blazorwasm`)

To set interactivity:
```powershell
dotnet new blazor --interactivity <Server|WebAssembly|Auto|None>
```

Interactivity options:
- `Server` = interactive SSR
- `WebAssembly` = client-side rendering
- `Auto` = automatic
- `None` = static SSR

Other options:
- Use `--empty` to omit sample pages and basic styling
- Use `--all-interactive` to include an interactive render mode at the top level

#### running the app
From the solution's server project (the project that doesn't end in `.Client`), compile and start the app:
```powershell
dotnet watch
```

Alternatively, to run the app with HTTPS, either:
```powershell
dotnet watch --launch-profile https
```

Or, in `Properties/launchSettings.json`, reorganize the launch profiles so that the `https` profile is above the `http` profile.

### .NET wasm build tools
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
