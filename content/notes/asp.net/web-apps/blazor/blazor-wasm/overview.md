---
title: notes > asp.net > web apps > blazor > blazor wasm > overview
date: 2023-04-17T00:00:00-06:00
draft: false
weight: -1
---

# Project Structure
`Program.cs` — entrypoint; host; startup
- Adds the root component (`App.razor`)

`├──App.razor` — the root component; sets up client-side routing using the Router component; Router intercepts browser navigation and renders the page that matches the requested address  
`├──_Imports.razor` — common namespaces made available to all Components
`├──wwwroot/` — the web root  
&emsp;`├──appsettings.json` — environment app settings  
&emsp;`└──index.html` — when any page of the app is initially requested, this page is rendered and returned in the response  
&emsp;&emsp;- This page defines a `<div>` that specifies where the root App component is rendered  
&emsp;&emsp;- `<head>` is located here  
`├──Shared/`  
&emsp;`├──MainLayout.razor` — the app's layout component  
&emsp;&emsp;`└──MainLayout.razor.css` — stylesheet for the above layout  
&emsp;`├──NavMenu.razor` — implements sidebar navigation; includes NavLink component which renders navigation links to other components  
&emsp;&emsp;`└──NavMenu.razor.css` — stylesheet for the above  
&emsp;`└──SurveyPrompt.razor` — Blazor survey component  
`├──Properties/launchSettings.json` — development environment configuration  
`├──Pages/`  
&emsp;`├──Counter.razor` — the Counter page  
&emsp;`├──Error.razor` — rendered when an unhandled exception occurs  
&emsp;`├──FetchData.razor` — the Fetch Data page  
&emsp;`└──Index.razor` — the home page  
`├──Data/` — `WeatherForecast` class and implementation of `WeatherForecastService` that provides example weather data to app's FetchData component.  

# Blazor WASM Hosted (`dotnet new blazorwasm --hosted`)
Includes these ASP.NET Core projects with these additional files:  
&emsp;`├──Client` — the Blazor WASM app  
&emsp;`├──Server` — serves the Blazor WASM app and weather data to clients  
&emsp;&emsp;`└──Controllers/WeatherForecastController.cs`  
&emsp;`├──Shared` — maintains common classes, methods and resources  
&emsp;&emsp;`└──WeatherForecast.cs`  
