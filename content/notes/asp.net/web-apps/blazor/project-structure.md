---
title: project structure
date: 2024-12-08T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/asp.net/web-apps/blazor/project-structure
---

# [Blazor Web App (template = `blazor`) project structure](https://learn.microsoft.com/en-us/aspnet/core/blazor/project-structure?view=aspnetcore-9.0)
Used for both server-side rendered (SSR) and client-side rendered (CSR) apps.
- If both interactive SSR and CSR are selected on app creation, the template uses the Interactive Auto render mode
- If Interactive WebAssembly is selected, the solution also includes an additional `.Client` project
  - The built output in this project is downloaded to and executed on the client
  - Components using Interactive WebAssembly or Interactive Auto must be located in the `.Client` project

For server-only projects:
- `/`
  - `Components/` — holds shared components
    - `Layout/`
      - `MainLayout.razor` — the app's layout component
        - `MainLayout.razor.css` — the stylesheet for the app's main layout
      - `NavMenu.razor` — implements sidebar navigation and includes `NavLink` components
        - `NavMenu.razor.css` — the stylesheet for the app's navigation menu
    - `Pages/` — contains app's routable server-side components; route for each page specified with `@page` directive
  - `Properties/`
    - `launchSettings.json` — development environment configuration
  - `wwwroot/` — the web root folder; holds app's public static assets
  - `_Imports.razor` — common Razor directives
  - `appsettings.json` or `appsettings.Development.json` — holds configuration settings
  - `App.razor`
    - The app's root component; the first component loaded
    - Contains `<head>` and `<body>` content and the Blazor `<script>` tag
  - `Routes.razor` — sets up routing using `Router` component
  - `Program.cs` — entry point; sets up ASP.NET Core web app host; contains startup logic, service registrations, configuration, logging, and request processing pipeline
    - `AddRazorComponents()` — adds services for Razor components
    - `AddInteractiveServerComponents()` — adds services for rendering Interactive Server components
    - `AddInteractiveWebAssemblyComponents()` — adds services for rendering Interactive WebAssembly components
    - `MapRazorComponents()` — discovers available components and specifies root component of app
    - `AddInteractiveServerRenderMode()` - configures interactive SSR mode
    - `AddInteractiveWebAssemblyRenderMode()` — configures interactive WebAssembly render mode

If a client project exists:
- `/.Client/`
  - `Layout/`
    - `MainLayout.razor` — the app's layout component
      - `MainLayout.razor.css` — the stylesheet for the app's main layout
    - `NavMenu.razor` — implements sidebar navigation and includes `NavLink` components
        - `NavMenu.razor.css` — the stylesheet for the app's navigation menu
  - `Pages/` — contains routable client-side components; route for each page specified with `@page` directive
  - `wwwroot/` — the web root folder; holds app's public static assets
    - `appsettings.json` or `appsettings.Development.json` — holds configuration settings
  - `_Imports.razor` — common Razor directives
  - `Program.cs` — entry point; sets up WASM host; contains startup logic, service registrations, configuration, logging, and request processing pipeline
  - `Routes.razor` — sets up routing using `Router` component

# Standalone Blazor WebAssembly (template = `blazorwasm`) project structure
  - `/`
    - `Layout/`
      - `MainLayout.razor` — the app's layout component
        - `MainLayout.razor.css` — the stylesheet for the app's main layout
      - `NavMenu.razor` — implements sidebar navigation and includes `NavLink` components
        - `NavMenu.razor.css` — the stylesheet for the app's navigation menu
    - `Pages/` — contains app's routable components; route for each page specified with `@page` directive
      - `Counter.razor` — implements the demo Counter page
      - `Index.razor` — implements the demo Home page
      - `Weather.razor` — implements the demo Weather page
    - `wwwroot/` — the web root folder; holds app's public static assets
      - `sample-data/`
        - `weather.json` — sample weather data
      - `appsettings.json` or `appsettings.Development.json` — holds configuration settings
      - `index.html` — the root page of the app implemented as an HTML page:
        - When any page is initially requested, this page is rendered and returned in the response
        - The page's `div` DOM element with `id` of `app` specifies where the root `App` component is rendered
        - Contains the Blazor `<script>` tag
        - Contains `<head>` and `<body>` content
    - `Properties/`
      - `launchSettings.json` — development environment configuration
    - `_Imports.razor` — common Razor directives
    - `App.razor` — the app's root component; the first component loaded; sets up client-side routing using the `Router` component
    - `Program.cs`
      - Entry point; sets up WASM host
      - The root component collection `builder.RootComponents.Add<App>("#app")` specifies that `App` is the root component and that it can be found in the `div` DOM collection with `id` of `app` in `wwwroot/index.html`