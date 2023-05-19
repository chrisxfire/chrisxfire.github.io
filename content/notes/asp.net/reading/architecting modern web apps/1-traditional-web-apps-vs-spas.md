---
title: "notes > asp.net > reading > architecting modern web apps > traditional web apps vs spas"
date: 2023-04-14T00:00:00-06:00
draft: false
---

From ["Architect Modern Web Applications with ASP.NET Core and Azure"][book] eBook

# Traditional Web Apps
- Perform most app logic on the server
- Choose when: 
	- Client-side requirements are simple (or even read-only) (search engines; blogs; CMS public-facing apps)
	- App needs to function in browsers without JavaScript

# Single Page Applications
- Perform most UI logic in web browser and communicate with the web server via APIs
- Using CI/CD may be more difficult
- Choose when:
	- App must expose a rich UI with many features
			§ SPAs load more quickly; user actions are more responsive
			§ SPAs support incremental updates, saving partially completed forms/docs; drag-and-drop; disconnected mode
	- Team is familiar with JavaScript / TypeScript / Blazor WASM
	- App must already expose an API for other clients

# Blazor (Blazor Server or Blazor WASM)
- Build rich UIs (like with SPA) but without significant JavaScript
- Choose when
	- App must expose a rich UI with many features
	- Team is more comfortable with .NET vs. JavaScript / TypeScript

[book]: https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/