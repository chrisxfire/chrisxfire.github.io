---
title: notes > asp.net > web apps > blazor > components > html <head> element components
date: 2023-07-11T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Some Razor Components modify the HTML `<head>` element's content of a page.

# HTML `<title>` Element and `PageTitle` Component
Set the page's title with a `PageTitle` component.  This renders the HTML `<title>` element to a `HeadOutlet` component:
```html
@page "/set-title"

<h1>Setting title</h1>

<p>Title: @title</p>

<PageTitle>@title</PageTitle>

```
```cs
@code {
    private string title = "Title set by component";
}
```

# HTML `<head>` Element and `HeadContent` Component
Set the content of the `<head>` element with a `HeadContent` component.  This provides content to a `HeadOutlet` component:
```html
@page "/control-head-content"

<h1>Control <head> content</h1>

<p>Title: @title</p>

<p>Description: @description</p>

<PageTitle>@title</PageTitle>

<HeadContent>
    <meta name="description" content="@description">
</HeadContent>
```
```cs
@code {
    private string description = "Description set by component";
    private string title = "Title set by component";
}
```

# `HeadOutlet` Component
Renders content provided by `HeadContent` and `PageTitle` components.

## In Blazor WASM
The `HeadOutlet` component is added to the `RootComponents` collection in `Program.cs`:
```cs
builder.RootComponents.Add<HeadOutlet>("head::after");
```

By using the `::after` pseudo-selector, contents of the root component appended to existing head contents instead of replacing them.

## In Blazor Server
A component tag helper in `Pages/_Host.cshtml` renders `<head>` content for the `HeadOutlet` component:
```html
<head>
    ...
    <component type="typeof(HeadOutlet)" render-mode="ServerPrerendered" />
</head>
```

# `NotFound` Component
The `NotFound` Component in the `App` Component (`App.razor`) sets the page title to "Not found":
```html
<PageTitle>Not found</PageTitle>
```
