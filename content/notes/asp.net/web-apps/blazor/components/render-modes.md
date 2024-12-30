---
title: render modes
date: 2024-12-06T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/asp.net/web-apps/blazor/components/render-modes
---

# [Overview](https://learn.microsoft.com/en-us/aspnet/core/blazor/components/render-modes?view=aspnetcore-9.0)
Starting in .NET 8, every component in Blazor web apps adopts a *render mode*. (Prior to .NET 8, only the hosting model concept applied). This mode determines the component's:
- Hosting model
- Render location (server, client)
- Interactivity (static on server, interactive on server, interactive on client)

# render modes

| Render Mode                                  | Description                                                         | Render location     | Interactive |
| -------------------------------------------- | ------------------------------------------------------------------- | ------------------- | ----------- |
| [Static - Server](#static-ssr)               | Static SSR                                                          | Server              | No          |
| [Interactive - Server](#interactive-ssr)     | Interactive SSR (via Blazor Server)                                 | Server              | Yes         |
| [Interactive - WASM](#client-side-rendering) | CSR (via Blazor Wasm)                                               | Client              | Yes         |
| [Interactive - Auto](#automatic-rendering)   | CSR initially w/Blazor Server then CSR after Blazor bundle download | Server, then client | Yes         |

# enabling interactive render modes
Blazor Web Apps must be configured for interactive render modes. This is done via component builder extensions:
- `AddInteractiveServerComponents` adds services to support rendering Interactive Server components.
- `AddInteractiveWebAssemblyComponents` adds services to support rendering Interactive WebAssembly components.
- `AddInteractiveServerRenderMode` configures interactive server-side rendering (interactive SSR) for the app.
- `AddInteractiveWebAssemblyRenderMode` configures the Interactive WebAssembly render mode for the app.

**These extensions are automatically applied** on the Blazor Web App project template.

## examples
1. Enable and configure interactive SSR:
    ```cs
    builder.Services.AddRazorComponents()
                    .AddInteractiveServerComponents();
    // ...
    app.MapRazorComponents<App>()
       .AddInteractiveServerRenderMode();
    ```

2. Enable and configure interactive WASM:
    ```cs
    builder.Services.AddRazorComponents()
                    .AddInteractiveWebAssemblyComponents();
    // ...
    app.MapRazorComponents<App>()
       .AddInteractiveWebAssemblyRenderMode();
    ``` 

3. Enable and configure interactive SSR, interactive WASM, and interactive Auto modes:
    ```cs
    builder.Services.AddRazorComponents()
                    .AddInteractiveServerComponents()
                    .AddInteractiveWebAssemblyComponents();
    // ...
    app.MapRazorComponents<App>()
       .AddInteractiveServerRenderMode()
       .AddInteractiveWebAssemblyRenderMode();
    ```

# applying render modes
## on component instances
Use the `@rendermode` Razor directive attribute: 
```cshtml
<Dialog @rendermode="InteractiveServer" />
<!-- 
    If Microsoft.AspNetCore.Components.Web.RenderMode is not imported, use this syntax instead:
    <Dialog @rendermode="RenderMode.InteractiveServer" />
 -->
```

## in component definitions
Render modes are commonly applied to component definitions when applying render modes to specific pages.

> [!NOTE] Routable pages use the same render mode as the Router component that rendered the page.

Use the `@rendermode` Razor directive:
```cshtml
@page "..."
@rendermode InteractiveServer
```

## on the entire app
The render mode cannot be set on the root component (usually `App`). Instead, specify the render mode at the highest-level interactive component that is not a root component. This is usually where the `Routes` component is used in `Components/App.razor`:
```cshtml
<Routes @rendermode="InteractiveServer" />
```

## programmatically
See https://learn.microsoft.com/en-us/aspnet/core/blazor/components/render-modes?view=aspnetcore-9.0&preserve-view=true#apply-a-render-mode-programatically

# Pre-rendering
*Pre-rendering* s the process of initially rendering page content on the server without enabling event handlers for rendered controls.
- The server outputs the HTML of the page ASAP after the initial request.
  - Makes the app feel more responsive.
  - Can also improve SEO.
- Always followed by final rendering, either on server or the client.

Pre-rendering is enabled by default for interactive components.

## disabling
### on component instances
Pass the `prerender` flag with a value of `false` to the render mode:

```cshtml
<... @rendermode="new InteractiveServerRenderMode(prerender: false)" />

<... @rendermode="new InteractiveWebAssemblyRenderMode(prerender: false)" />

<... @rendermode="new InteractiveAutoRenderMode(prerender: false)" />
```

### in component definitions
```cshtml
@rendermode @(new InteractiveServerRenderMode(prerender: false))

@rendermode @(new InteractiveWebAssemblyRenderMode(prerender: false))

@rendermode @(new InteractiveAutoRenderMode(prerender: false))
```

### on the entire app
specify the render mode at the highest-level interactive component that is not a root component. This is usually where the `Routes` component is used in `Components/App.razor`:

```cshtml
<Routes @rendermode="new InteractiveServerRenderMode(prerender: false)" />
```

And in the `HeadOutlet` component in the `App` component:
```cshtml
<HeadOutlet @rendermode="new InteractiveServerRenderMode(prerender: false)" />
```

# Detecting render mode, render location, interactivity
Use the `ComponentBase.RendererInfo` and `ComponentBase.AssignedRenderMode` properties:
- `RendererInfo.Name` returns:
  - `Static`: On the server (SSR) and incapable of interactivity.
  - `Server`: On the server (SSR) and capable of interactivity after pre-rendering.
  - `WebAssembly`: On the client (CSR) and capable of interactivity after pre-rendering.
  - `WebView`: On the native device and capable of interactivity after pre-rendering.
- `RendererInfo.IsInteractive` is `true` when rendering interactively and `false` when pre-rendering or for static SSR.
- `AssignedRenderMode` returns:
  - `InteractiveServer` for Interactive Server.
  - `InteractiveAuto` for Interactive Auto.
  - `InteractiveWebAssembly` for Interactive WebAssembly.

## common use examples
1. Display content until a component is interactive:
    ```cshtml
    @if (!RendererInfo.IsInteractive)
    {
        <p>Connecting to the assistant...</p>
    }
    else
    {
        ...
    }
    ```
2. Disable a button until a component is active:
    ```cshtml
    <button @onclick="Send" disabled="@(!RendererInfo.IsInteractive)">
        Send
    </button>
    ```
3. Disable a form during pre-rendering and enable it when the component is interactive:
    ```cshtml
    <EditForm Model="Movie" ...>
        <fieldset disabled="@disabled">

            ...

            <button type="submit" >Save</button>
        </fieldset>
    </EditForm>

    @code {
        private bool disabled = true;

        [SupplyParameterFromForm]
        private Movie? Movie { get; set; }

        protected override async Task OnInitializedAsync()
        {
            Movie ??= await ...;

            if (RendererInfo.IsInteractive)
            {
                disabled = false;
            }
        }
    }
    ```

# static ssr
In static SSR, the component renders to the response stream. There is no interactivity.

Consider this component:
```cshtml
@page "/render-mode-1"

<button @onclick="UpdateMessage">Click me</button> @message

@code {
    private string message = "Not updated yet.";

    private void UpdateMessage()
    {
        message = "Somebody updated me!";
    }
}
```

Since there's no designation for this component's render mode, it inherits it from its parent.  
Since no parent/ancestor specifies a render mode, the component is statically rendered.  
Since it's statically rendered:
- The button isn't interactive
- The button doesn't call the `UpdateMessage` method when selected
- The value of `message` doesn't change
- The component isn't re-rendered in response to UI events.

## no blazor features for routing and authorization
In static SSR, Razor component page requests are processed by the server-side ASP.NET Core middleware pipeline.
Blazor features for routing/authorization are not available, including `NotAuthorized` and `NotFound` features in the `Routes` component.

# interactive ssr
In interactive SSR, the component renders interactively from the server using Blazor Server.

Consider this component:
```cshtml
@page "/render-mode-2"
@rendermode InteractiveServer

<button @onclick="UpdateMessage">Click me</button> @message

@code {
    private string message = "Not updated yet.";

    private void UpdateMessage()
    {
        message = "Somebody updated me!";
    }
}
```

In this component:
- The render mode is set in the component definition
- The button calls the `UpdateMessage` method when selected
- The value of `message` changes
- The component re-renders to update the message

# Client-side rendering (CSR)
In CSR, the component renders interactively on the client using Blazor Wasm. The .NET runtime and app bundle are downloaded
and cached when the WASM component is initially rendered.

Consider this component (identical to the previous example):
```cshtml
@page "/render-mode-3"
@rendermode InteractiveWebAssembly

<button @onclick="UpdateMessage">Click me</button> @message

@code {
    private string message = "Not updated yet.";

    private void UpdateMessage()
    {
        message = "Somebody updated me!";
    }
}
```

This component behaves identically as in the previous example. 

# automatic rendering
Auto rendering determines how to render the component at runtime. The component is initially rendered via interactive SSR. The 
.NET runtime and app bundle are downloaded to the client in the background and cached. 

> [!NOTE] The Auto render mode never dynamically changes the render mode of a component already on the page.

Auto mode initially decides which type of interactivity to use for a component. The component keeps that type as long as it's on the page.

Consider this component (identical to the previous example):
```cshtml
@page "/render-mode-4"
@rendermode InteractiveAuto

<button @onclick="UpdateMessage">Click me</button> @message

@code {
    private string message = "Not updated yet.";

    private void UpdateMessage()
    {
        message = "Somebody updated me!";
    }
}
```

This component behaves identically as in the previous example.

# render mode propagation
Render modes always propagate down the component hierarchy. 
- The default is Static
- `InteractiveServer`, `InteractiveWebAssembly`, and `InteractiveAuto` modes can be propagated from a parent component
- A child component cannot have a different *interactive* render mode (e.g. an `InteractiveServer` component cannot be a child of a `InteractiveWebAssembly` component).

> [!WARNING] Parameters passed to an interactive child component from a Static parent must be JSON serializable: you cannot pass
> render fragments or child content from a static parent to an interactive child.

Consider this component non-page, non-routable component:

`SharedMessage.razor`  
```cshtml
<p>@Greeting</p>

<button @onclick="UpdateMessage">Click me</button> @message

<p>@ChildContent</p>

@code {
    private string message = "Not updated yet.";

    [Parameter]
    public RenderFragment? ChildContent { get; set; }

    [Parameter]
    public string Greeting { get; set; } = "Hello!";

    private void UpdateMessage()
    {
        message = "Somebody updated me!";
    }
}
```

Suppose the `SharedMessage` component placed in a statically-rendered parent component:
```cshtml
@page "/render-mode-5"

<SharedMessage />
```

In this case:
- The `SharedMessage` component is also statically rendered
- The button doesn't call `UpdateMessage`
- The `message` is not updated

Suppose the `SharedMessage` component is placed in a component that defines its render mode:
```cshtml
@page "/render-mode-6"
@rendermode InteractiveServer

<SharedMessage />
```

In this case:
 - The `SharedMessage` component is interactive
 - The button calls `UpdateMessage`
 - The `message` is updated

# Static SSR pages in a globally-interactive app
See https://learn.microsoft.com/en-us/aspnet/core/blazor/components/render-modes?view=aspnetcore-9.0&preserve-view=true#static-ssr-pages-in-a-globally-interactive-app

# Client-side services fail to resolve during pre-rendering
See https://learn.microsoft.com/en-us/aspnet/core/blazor/components/render-modes?view=aspnetcore-9.0&preserve-view=true#client-side-services-fail-to-resolve-during-prerendering

