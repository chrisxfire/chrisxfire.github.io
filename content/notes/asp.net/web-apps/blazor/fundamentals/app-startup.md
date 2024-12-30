---
title: app startup
date: 2023-04-18T00:00:00-06:00
draft: false
weight: 1
---

# [Overview](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/startup?view=aspnetcore-9.0&)
Startup is asynchronous and automatic via `blazor.web|server|webassembly.js`.

# manually starting blazor
## manually starting blazor web app
1. Add `autostart="false"` to the Blazor `<script>` tag.  
2. Place a script that calls `Blazor.start()` after the `<script>` tag inside the closing `<body>` tag.
3. Place static SSR options in the `ssr` property.
4. Place server-side Blazor SignalR circuit options in the `circuit` property.
5. Place client-side WebAssembly options in the `webAssembly` property.

```js
<script src="{BLAZOR SCRIPT}" autostart="false"></script>
<script>
  ...
  Blazor.start({
    ssr: {
      ...
    },
    circuit: {
      ...
    },
    webAssembly: {
      ...
    }
  });
  ...
</script>
```

## manually starting standalone blazor wasm and blazor server
1. Add `autostart="false"` to the Blazor `<script>` tag.  
2. Place a script that calls `Blazor.start()` after the `<script>` tag inside the closing `<body>` tag.
3. Add any options in the `Blazor.start()` parameter.

```js
<script src="{BLAZOR SCRIPT}" autostart="false"></script>
<script>
  ...
  Blazor.start({
    ...
  });
  ...
</script>
```

# javascript initializers
JS initializers execute logic before and after a Blazor app loads.

More: https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/startup?view=aspnetcore-9.0#javascript-initializers

# initialize blazor when the document is ready
```js
<script src="{BLAZOR SCRIPT}" autostart="false"></script>
<script>
  document.addEventListener("DOMContentLoaded", function() {
    Blazor.start();
  });
</script>
```

# chain to the promise from a manual start
See https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/startup?view=aspnetcore-9.0&preserve-view=true#chain-to-the-promise-that-results-from-a-manual-start

# Load Client-side Boot Resources
See https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/startup?view=aspnetcore-9.0&preserve-view=true#load-client-side-boot-resources

# Control Headers in C# Code
See https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/startup?view=aspnetcore-9.0&preserve-view=true#control-headers-in-c-code

# Client-side Loading Progress Indicators
See https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/startup?view=aspnetcore-9.0&preserve-view=true#client-side-loading-progress-indicators

# Configure the .NET WebAssembly Runtime
See https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/startup?view=aspnetcore-9.0&preserve-view=true#configure-the-net-webassembly-runtime

# disable enhanced navigation and form handling
See https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/startup?view=aspnetcore-9.0&preserve-view=true#disable-enhanced-navigation-and-form-handling

