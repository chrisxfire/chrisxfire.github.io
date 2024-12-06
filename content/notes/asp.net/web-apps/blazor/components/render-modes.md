---
title: render modes
date: 2024-12-06T00:00:00-06:00
draft: true
weight: 1
tags:
 - kb/asp.net/web-apps/blazor/components/render-modes
---

# [Overview](https://learn.microsoft.com/en-us/aspnet/core/blazor/components/render-modes?view=aspnetcore-9.0)
Starting in .NET 8, every component in Blazor web apps adopts a *render mode*. (Prior to .NET 8, only the hosting model concept applied). This mode determines the component's:
- Hosting model
- Render location (server, client)
- Interactivity (static on server, interactive on server, interactive on client)

# Render Modes

| Render Mode          | Description                                                         | Render location     | Interactive |
| -------------------- | ------------------------------------------------------------------- | ------------------- | ----------- |
| Static - Server      | Static SSR                                                          | Server              | No          |
| Interactive - Server | Interactive SSR (via Blazor Server)                                 | Server              | Yes         |
| Interactive - WASM   | CSR (via Blazor Wasm)                                               | Client              | Yes         |
| Interactive - Auto   | CSR initially w/Blazor Server then CSR after Blazor bundle download | Server, then client | Yes         |

# Enabling Interactive Render Modes
Blazor Web Apps must be configured for interactive render modes. This is done via component builder extensions:
- `AddInteractiveServerComponents` adds services to support rendering Interactive Server components.
- `AddInteractiveWebAssemblyComponents` adds services to support rendering Interactive WebAssembly components.
- `AddInteractiveServerRenderMode` configures interactive server-side rendering (interactive SSR) for the app.
- `AddInteractiveWebAssemblyRenderMode` configures the Interactive WebAssembly render mode for the app.

**These extensions are automatically applied** on the Blazor Web App project template.

## Examples
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

# Applying Render Modes
## On Component Instances
Use the `@rendermode` Razor directive attribute: 
```cshtml
<Dialog @rendermode="InteractiveServer" />
<!-- 
    If Microsoft.AspNetCore.Components.Web.RenderMode is not imported, use this syntax instead:
    <Dialog @rendermode="RenderMode.InteractiveServer" />
 -->
```

## In Component Definitions
Render modes are commonly applied to component definitions when applying render modes to specific pages.

> [!NOTE]
> Routable pages use the same render mode as the Router component that rendered the page.

Use the `@rendermode` Razor directive:
```cshtml
@page "..."
@rendermode InteractiveServer
```

## On the Entire App
The render mode cannot be set on the root component (usually `App`). Instead, specify the render mode at the highest-level interactive component that is not a root component. This is usually where the `Routes` component is used in `Components/App.razor`:
```cshtml
<Routes @rendermode="InteractiveServer" />
```

# Pre-rendering
*Pre-rendering* s the process of initially rendering page content on the server without enabling event handlers for rendered controls.
- The server outputs the HTML of the page ASAP after the initial request.
  - Makes the app feel more responsive.
  - Can also improve SEO.
- Always followed by final rendering, either on server or the client.

Pre-rendering is enabled by default for interactive components.

## Disabling
### On Component Instances
Pass the `prerender` flag with a value of `false` to the render mode:

```cshtml
<... @rendermode="new InteractiveServerRenderMode(prerender: false)" />

<... @rendermode="new InteractiveWebAssemblyRenderMode(prerender: false)" />

<... @rendermode="new InteractiveAutoRenderMode(prerender: false)" />
```

### In Component Definitions
```cshtml
@rendermode @(new InteractiveServerRenderMode(prerender: false))

@rendermode @(new InteractiveWebAssemblyRenderMode(prerender: false))

@rendermode @(new InteractiveAutoRenderMode(prerender: false))
```

### On the Entire App
specify the render mode at the highest-level interactive component that is not a root component. This is usually where the `Routes` component is used in `Components/App.razor`:

```cshtml
<Routes @rendermode="new InteractiveServerRenderMode(prerender: false)" />
```

And in the `HeadOutlet` component in the `App` component:
```cshtml
<HeadOutlet @rendermode="new InteractiveServerRenderMode(prerender: false)" />
```

## Programmatically
See https://learn.microsoft.com/en-us/aspnet/core/blazor/components/render-modes?view=aspnetcore-9.0&preserve-view=true#apply-a-render-mode-programatically

# Detecting Render Mode, Render Location, Interactivity
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

## Common Use Examples
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

# Static SSR
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

## No Blazor Features for Routing and Authorization
In static SSR, Razor component page requests are processed by the server-side ASP.NET Core middleware pipeline.
Blazor features for routing/authorization are not available, including `NotAuthorized` and `NotFound` features in the `Routes` component.

