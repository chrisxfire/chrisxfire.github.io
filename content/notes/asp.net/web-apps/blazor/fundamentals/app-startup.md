---
title: notes > asp.net > web apps > blazor > fundamentals > app startup
date: 2023-04-18T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Startup is asynchronous and automatic via blazor.server.js or blazor.webassembly.js.  The Blazor `<script>` tag is in `wwwroot/index.html` (WASM) or `Pages/_Host.cshtml` (Server).
- Documentation: https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/startup?view=aspnetcore-7.0

# Manually Starting Blazor
Add `autostart="false"` to the Blazor `<script>` tag.  
Place a script that calls `Blazor.start()` after the `<script>` tag inside the closing `<body>` tag.

# JavaScript Initializers
JS initializers execute logic before and after a Blazor app loads.

More: https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/startup?view=aspnetcore-7.0#javascript-initializers