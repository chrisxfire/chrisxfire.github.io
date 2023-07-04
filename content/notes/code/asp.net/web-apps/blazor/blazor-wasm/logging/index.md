---
title: notes > code > asp.net > web apps > blazor > blazor wasm > logging
date: 2023-04-18T00:00:00-06:00
draft: false
---

# [Overview](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/logging?view=aspnetcore-7.0)
Without additional configuration, Blazor WASM apps log to client-side browser developer tools at `LogLevel.Information` or higher.

Logging in `Program.cs`  
After `WebAssemblyHostBuilder` is built:
```cs
var host = builder.Build();

var logger = host.Services.GetRequiredService<ILoggerFactory>()
    .CreateLogger<Program>();

logger.LogInformation("Logged after the app is built in Program.cs.");

await host.RunAsync();
```

# Configure Logging
Use the `WebAssemblyHostBuilder.Logging` property.

Log Categories, log event IDs, log message templates, log exception parameters, filter functions, and custom logger providers are supported in Blazor WASM.

The Blazor WASM developer tools console logger does not support log scopes.  A custom logger can.

# [Hosted Blazor WASM Logging](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/logging?view=aspnetcore-7.0#hosted-blazor-webassembly-logging)
A hosted Blazor WebAssembly app that prerenders its content executes component initialization code twice. Logging takes place server-side on the first execution of initialization code and client-side on the second execution of initialization code. Depending on the goal of logging during initialization, check logs server-side, client-side, or both.

# [SignalR Client Logging](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/logging?view=aspnetcore-7.0#signalr-client-logging-blazor-webassembly)

# [Authentication Logging](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/logging?view=aspnetcore-7.0#authentication-logging-blazor-webassembly)
