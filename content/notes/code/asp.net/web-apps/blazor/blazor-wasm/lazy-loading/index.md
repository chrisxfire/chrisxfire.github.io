---
title: notes > code > asp.net > web apps > blazor > blazor wasm > lazy loading
date: 2023-05-12T00:00:00-07:00
draft: false
weight: 1
---

# Overview
By default, when the app launches, all assemblies are automatically downlaoded from the web server. Blazor can be instructed to postpone downloading an assembly.

# Implementation Steps
## 1. Register the Lazily-Loaded Assemblies in Project File
`csproj`  
```xml
<ItemGroup>
    <BlazorWebAssemblyLazyLoad Include="ExampleProject.dll" />
</ItemGroup>
```

## 2. Make Changes to Router in `App.razor`
`App.razor`
```html
<!-- Inject LazyAssemblyLoader which is automatically registered with DI by the framework -->
@using Microsoft.AspNetCore.WebAssembly.Services
@inject LazyAssemblyLoader

<Router AppAssembly="@typeof(App).Assembly" AdditionalAssemblies="@lazyLoadedAssemblies"
        OnNavigateAsync="@OnNavigateAsync">
    ...
</Router>
```
```cs
@code
{
    private List<Assembly> lazyLoadedAssemblies = new();

    private async Task OnNavigateAsync(NavigationContext args)
    {
        // check if we are navigating to the detail page for the first time
        if (args.path.Contains("employeedetail"))
        {
            // use js-interop to make an async network call and retrieve the
            // array of assemblies to be loaded lazily:
            var assemblies = await LazyAssemblyLoader.LoadAssembliesAsync(
                new string[] { "BethanysPieShop.ComponentsLibrary.dll" }
            )
            
            // add those assemblies to the List<Assembly>:
            lazyLoadAssemblies.AddRange(assemblies);
        }
    }
}
```
