---
title: "notes > asp.net > core > app startup"
date: 2023-05-14T00:00:00-07:00
draft: false
---

# Overview
This template supports Razor Pages, MVC controllers with views, Web API controllers, and Minimial APIs app models.
- Configures required services
    - `ILogger<T>` is provided by the ASP.NET framework
- Creates the request handling pipeline via middleware

`Program.cs`
```cs
var builder = WebApplication.CreateBuilder(args); // Configures Kestrel

// Add services to the container.
builder.Services.AddRazorPages(); // For a Razor Pages client-side Web UI
builder.Services.AddControllersWithViews(); // For an MVC client-side Web UI

var app = builder.Build();

// Configure the HTTP request pipeline.
if (!app.Environment.IsDevelopment())
{
    app.UseExceptionHandler("/Error");
    app.UseHsts(); // Default HSTS value is 30 days; change for production scenarios; https://aka.ms/aspnetcore-hst
}

app.UseHttpsRedirection(); // Redirect HTTP requests to HTTPS
app.UseStaticFiles(); // Enable serving of static files (HTML, CSS, images, JavaScript)

app.UseAuthorization(); 

app.MapGet("/hi", () => "Hello!");

app.MapDefaultControllerRoute();
app.MapRazorPages(); // Configure endpoint routing for Razor Pages

app.Run();
```

# [Extending Startup with Startup Filters](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/startup?view=aspnetcore-7.0#extend-startup-with-startup-filters)
TODO...