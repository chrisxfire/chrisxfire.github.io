---
title: dev tunnels
date: 2023-10-03T00:00:00-06:00
draft: false
weight: 1
---

# Overview [[Documentation](https://learn.microsoft.com/en-us/aspnet/core/test/dev-tunnels?view=aspnetcore-7.0)]  

<g>Availability</g>: Visual Studio 2022 17.6+ w/*ASP.NET and web development* workload installed

Dev Tunnels are a Visual Studio 2022 feature that create ad-hoc connections between machines that cannot directly connect to one another. A URL is created that enables any device with an internet connection to connect to the ASP.NET Core project while it runs on localhost.

Uses:
* Testing a web app on other devices
* Testing an app with external services
* Making an app temporarily available for presentation

# Tunnel Options
Tunnel types:
- *Temporary* tunnels get a new URL each time Visual Studio is started.
- *Persistent* tunnels get the same URL each time Visual Studio is started.

Tunnel access:
- *Private* —  the tunnel is only accessible on the account that created it
- *Organization* — the tunnel is accessible to accounts in the same organization as the one that created it
  - Note: If *Organization* is selected for a personal Microsoft account, this has the same effect as *Private*
- *Public* — anyone can access the tunnel

# Creating Dev Tunnels
Visual Studio > Debug toolbar > Web server control dropdown > Dev Tunnels > **Create A Tunnel...**

Enter a **name**, **tunnel type**, and **tunnel access**.  Click **OK**.  A web browser will open to the tunnel URL.

Tip: select the QR Code icon on the browser's URL bar to create a QR code to the tunnel.

# Dev Tunnels Tool Window
View > *Other Windows* > **Dev Tunnels**
- **Clear Active Tunnel** — disables a tunnel
- **Make Active Tunnel** — enables a tunnel
- **Copy Tunnel Access Token** — copies the active tunnel's access token to the clipboard

# Tunnel Access Tokens
When a tunnel is created with *Private* or *Organization* access, and the app is a web API, the token must be provided to authenticate to the tunnel. Include the following header in the request:
```
X-Tunnel-Authorization tunnel <TOKEN>
```

# Tunnel URL Environment Variables
When an app is launched that uses a tunnel, Visual Studio creates the `VS_TUNNEL_URL` environment variable.

If there are multiple ASP.NET Core projects configured as the startup project, for all subsequent projects after the first, the variable name is `VS_TUNNEL_URL_{ProjectName}`.