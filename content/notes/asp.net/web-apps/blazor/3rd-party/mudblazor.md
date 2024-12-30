---
title: mudblazor
date: 2023-06-12T00:00:00-06:00
draft: false
weight: 1
---

# overview
A Blazor Component library.

See also:  https://try.mudblazor.com

# installation
## direct
```powershell
dotnet add package MudBlazor
```

## via template
Blazor template preconfigured with MudBlazor:

```powershell
dotnet new --install MudBlazor.Templates
dotnet new mudblazor --host wasm --name AppName
```

# getting started
## 1. Add imports
`_Imports.razor`
```html
@using MudBlazor
```

`index.html` (Blazor WASM) or `_Host.cshtml` (Blazor Server)
```html
<link href="https://fonts.googleapis.com/css?family=Roboto:300,400,500,700&display=swap" rel="stylesheet" />
<link href="_content/MudBlazor/MudBlazor.min.css" rel="stylesheet" />
<!-- ... -->
<script src="_content/MudBlazor/MudBlazor.min.js"></script>
```

## 2. Remove Bootstrap
The Bootstrap components that are loaded by Blazor's default template are no longer needed:
1. Delete the `bootstrap/` folder
2. Delete the `open-iconic/` folder
3. Empty or delete `site.css`

## 3. Register Services
`Program.cs`
```cs
using MudBlazor.Services;

builder.Services.AddMudServices();
```

## 4. Add Components
`MainLayout.razor`
```html
<!-- Required: -->
<MudThemeProvider/>
<!-- Optional: -->
<MudDialogProvider/>
<MudSnackbarProvider/>
```

# layouts
## layout providers
1. `MudThemeProvider` — provides theme settings such as colors, fonts, shadows, and other properties.  
2. `MudDialogProvider`.
3. `MudSnackbarProvider`.

## basic layout
`MudLayout` should be placed in `MainLayout.razor`.  Inside a `MudLayout` Component:
- Place `MudAppBar` and `MudDrawer` before `MudMainContent` (below) so they are included in all pages
- Place `MudMainContent`, which is where the page body resides.  Example:

`MainLayout.razor`
```html
@inherits LayoutComponentBase

<MudThemeProvider/>
<MudDialogProvider/>
<MudSnackbarProvider/>

<MudLayout>
    <MudAppBar>
        My Application
    </MudAppBar>
    <MudDrawer Open="true">

    </MudDrawer>
    <MudMainContent>
        @Body
    </MudMainContent>
</MudLayout>
```

## functionality
Add a MudIconButton to open/close the MudDrawer and a NavMenu for basic navigation:
`MainLayout.razor`
```html
@inherits LayoutComponentBase

<MudThemeProvider />
<MudDialogProvider />
<MudSnackbarProvider />

<MudLayout>
    <MudAppBar>
        <MudIconButton Icon="@Icons.Material.Filled.Menu" Color="Color.Inherit" Edge="Edge.Start" OnClick="@((e) => DrawerToggle())" />
        My Application
    </MudAppBar>
    <MudDrawer @bind-Open="@_drawerOpen">
        <MyNavMenu/>
    </MudDrawer>
    <MudMainContent>
        @Body
    </MudMainContent>
</MudLayout>
```
```cs
@code {
    bool _drawerOpen = true;

    void DrawerToggle()
    {
        _drawerOpen = !_drawerOpen;
    }
}
```

`NavMenu.razor`
```html
<MudNavMenu>
    <MudNavLink Href="/" Match="NavLinkMatch.All">Dashboard</MudNavLink>
    <MudNavLink Href="/servers" Match="NavLinkMatch.Prefix">Servers</MudNavLink>
    <MudNavGroup Title="Settings" Expanded="true">
        <MudNavLink Href="/users"  Match="NavLinkMatch.Prefix">Users</MudNavLink>
        <MudNavLink Href="/security"  Match="NavLinkMatch.Prefix">Security</MudNavLink>
    </MudNavGroup>
    <MudNavLink Href="/about"  Match="NavLinkMatch.Prefix">About</MudNavLink>
</MudNavMenu>
```

## Content & Containers
Use `MudContainer` to center some content and add gutters to a page.  This can be done either in `MainLayout.razor` or an individual page:

`SomePage.razor`
```html
@inherits LayoutComponentBase

<MudMainContent>
    <MudContainer MaxWidth="MaxWidth.Medium">
        @Body
    </MudContainer>
</MudMainContent>
```

# wireframes
Wireframes are small templates created by the MudBlazor team to serve as a starting point:

https://mudblazor.com/getting-started/wireframes
