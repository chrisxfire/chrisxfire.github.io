---
title: "notes > asp.net > reading > architecting modern web apps > develop asp.net core mvc apps > client communication"
date: 2023-04-14T00:00:00-06:00
draft: false
---

ASP.NET Core apps, aside from serving pages and responding to requests via web APIs, can also communicate directly with connected clients.  This is usally done via WebSockets.  SignalR is a library that implements WebSockets and other transport technologies.

Use cases:
- Live chat apps
- Monitoring apps
- job progress updates
- Notifications
- Interactive forms apps
