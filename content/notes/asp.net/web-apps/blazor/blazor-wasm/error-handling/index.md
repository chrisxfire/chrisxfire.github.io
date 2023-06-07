---
title: notes > asp.net > web apps > blazor > blazor wasm > error handling
date: 2023-04-18T00:00:00-06:00
draft: false
---

# Overview
During development, when Blazor apps encounter an error, it displays a light yellow bar the bottom of the screen.
Customize it in `wwwroot/index.html`:
```html
<div id="blazor-error-ui">
    An unhandled error has occurred.
    <a href="" class="reload">Reload</a>
    <a class="dismiss">🗙</a>
</div>
```
