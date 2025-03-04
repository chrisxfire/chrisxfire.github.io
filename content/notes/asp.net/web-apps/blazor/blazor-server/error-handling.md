---
title: error handling
date: 2023-04-18T00:00:00-06:00
draft: false
weight: 1
---

# overview
During development, when Blazor apps encounter an error, it displays a light yellow bar the bottom of the screen.
Customize it in `Pages/_Host.cshtml`:
```html
<div id="blazor-error-ui">
    <environment include="Staging,Production">
        An error has occurred. This application may no longer respond until reloaded.
    </environment>
    <environment include="Development">
        An unhandled exception has occurred. See browser dev tools for details.
    </environment>
    <a href="" class="reload">Reload</a>
    <a class="dismiss">🗙</a>
</div>
```

# detailed circuit errors
To get detailed circuit errors, set `CircuitOptions.DetailedErrors` to `true`, or set the `DetailedErrors` configuration key to true in `appsettings.Development.json.`  Set SignalR server-side logging to `Debug` or `Trace`:
`appsettings.Development.json`
```json
{
    "DetailedErrors": true,
    "Logging": {
    "LogLevel": {
        "Default": "Information",
        "Microsoft": "Warning",
        "Microsoft.Hosting.Lifetime": "Information",
        "Microsoft.AspNetCore.SignalR": "Debug"
    }
    }
}
```
