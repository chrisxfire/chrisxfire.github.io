---
title: rendering
date: 2024-12-06T00:00:00-06:00
draft: true
weight: 1
tags:
 - kb/asp.net/web-apps/blazor/rendering
---

# [overview](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/?view=aspnetcore-9.0)
To *render* means to produce the HTML markup that browsers display. 
Razor components are either *statically* or *interactively* rendered, and rendered either *client-side* or *server-side*.

# rendering concepts
## static vs. interactive rendering
- Static rendering — always server-side
  - The component is rendered without interaction between the user and .NET/C# code.
  - JavaScript and DOM events process normally, but no user events on the client can be processed.
- Interactive rendering
  - The component can process .NET events via C# code.
  - Server-side 
    - by the ASP.NET Core runtime
  - Client-side
    - in the browser (in the Blazor WASM runtime)

## pre-rendering
The process of initially rendering page content on the server without event handlers for rendered controls.
See [here](../components/render-modes.md#pre-rendering) for more information.

# more information
See [render modes](../components/render-modes.md).