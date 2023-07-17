---
title: notes > asp.net > web apps > blazor > blazor server > app startup
date: 2023-05-04T00:00:00-06:00
draft: false
weight: 1
---

# Overview
`Program.cs`
```cs
builder.Services.AddRazorPages();
builder.Services.AddServerSideBlazor(); // add Blazor services to the DI container
…
app.MapBlazorHub(); // set up an endpoint for the real-time communication w/browser (via SignalR)
app.MapFallbackToPage("/_Host"); // set the root page (Pages/_Host.cshtml) and enable nav; when no matching endpoint is found, route requests here
```

# Controlling Headers
Use middleware to control the headers collection:
```cs
Program.cs
app.Use(async (context, next) =>
{
	context.Response.Headers.Add("Content-Security-Policy", "{POLICY STRING}");
	await next();
});
```
