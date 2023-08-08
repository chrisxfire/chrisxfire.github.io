---
title: overview
date: 2023-04-17T00:00:00-06:00
draft: false
weight: -1
---

# Project Structure
`├──Program.cs` — entrypoint; host; startup
- Calls `MapBlazorHub` to set up an endpoint for the real-time communication w/browser (via SignalR)
- Calls `MapFallbackToPage("/_Host")` to set the root page (`Pages/_Host.cshtml`) and enable nav.  

`├──appsettings.json` — environmental app settings  
`├──App.razor` — the root component
- Sets up client-side routing using the Router component; 
- Router intercepts browser navigation and renders the page that matches the requested address

`├──_Imports.razor` — global namespaces made available to all components  
`├──wwwroot` — the web root  
`├──Shared/`  
&emsp;`├──MainLayout.razor` — the app's layout component   
&emsp;&emsp;`└──MainLayout.razor.css` — stylesheet for the above layout  
&emsp;`└──NavMenu.razor` — implements sidebar navigation; includes NavLink component which renders navigation links to other components  
&emsp;&emsp;`└──NavMenu.razor.css` — stylesheet for the above  
&emsp;`└──SurveyPrompt.razor` — Blazor survey component  
`├──Properties/launchSettings.json` — development environment configuration  
`├──Pages/` — Blazor components are hosted here  
&emsp;`└──_Host.cshtml` — root page of the app;  
&emsp;&emsp;&emsp;- When any page is initially requested, this page is rendered and returned in the response;  
&emsp;&emsp;&emsp;- Specifies where the root component (`App.razor`) is rendered  
&emsp;&emsp;&emsp;- `<head>` is located here  
&emsp;&emsp;&emsp;- References _Layout  
&emsp;`├──_Layout.cshtml`  
&emsp;&emsp;- `@RenderBody()` is located here  
&emsp;&emsp;- References `_framework/blazor.server.js` (establishes SignalR connection)  
&emsp;`└──Counter.razor` — the Counter page  
&emsp;`└──Error.razor` — rendered when an unhandled exception occurs  
&emsp;`└──FetchData.razor` — the Fetch Data page  
&emsp;`└──Index.razor` — the home page  
`Data/` — `WeatherForecast` class and implementation of `WeatherForecastService` that provides example weather data to app's `FetchData` component.
