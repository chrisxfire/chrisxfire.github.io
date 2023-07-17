---
title: notes > asp.net > web apps > blazor > blazor wasm > app startup
date: 2023-04-18T00:00:00-06:00
draft: false
weight: 1
---

# [Loading Boot Resources](https://learn.microsoft.com/en-us/aspnet/core/blazor/fundamentals/startup?view=aspnetcore-7.0#load-boot-resources)
# Controlling Headers
Use middleware to control the headers collection:  
`Program.cs`
```cs
app.Use(async (context, next) =>
{
    context.Response.Headers.Add("Content-Security-Policy", "{POLICY STRING}");
    await next();
});
```
In hosted Blazor WASM apps, pass `StaticFileOptions` to `MapFallbackToFile` that specifies response headers:  
Server project's `Program.cs`:
```cs
var staticFileOptions = new StaticFileOptions
{
    OnPrepareResponse = context =>
    {
        context.Context.Response.Headers.Add("Content-Security-Policy", 
            "{POLICY STRING}");
    }
};

...

app.MapFallbackToFile("index.html", staticFileOptions);
```

# Loading Progress Indicators
Blazor WASM project template contains SVG and text indicators to show loading progress.  These are implemented with HTML and CSS using two CSS custom properties provided by Blazor WASM.

To create custom indicators:
```js
// resourcesLoaded is an instantaneous count of resources loaded during startup
// totalResources is the number of resources to load
const percentage = resourcesLoaded / totalResources * 100;
document.documentElement.style.setProperty(
  '--blazor-load-percentage', `${percentage}%`);
document.documentElement.style.setProperty(
  '--blazor-load-percentage-text', `"${Math.floor(percentage)}%"`);
```

The default round progress indicator is in `wwwroot/index.html.`  To implement a linear progress indicator:  
`wwwroot/css/app.css`
```css
.linear-progress {
    background: silver;
    width: 50vw;
    margin: 20% auto;
    height: 1rem;
    border-radius: 10rem;
    overflow: hidden;
    position: relative;
}

.linear-progress:after {
    content: '';
    position: absolute;
    inset: 0;
    background: blue;
    scale: var(--blazor-load-percentage, 0%) 100%; <!-- blazor-load-percentage is updated automatically -->
    transform-origin: left top;
    transition: scale ease-out 0.5s;
}
```
