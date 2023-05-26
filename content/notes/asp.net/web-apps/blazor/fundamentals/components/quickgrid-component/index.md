---
title: "notes > asp.net > web apps > blazor > fundamentals > components > quickgrid component"
date: 2023-05-26T00:00:00-06:00
draft: false
---

# Overview
`QuickGrid` is an experimental Component for quickly displaying data in tabular form.  It is highly optimized.

`QuickGrid` is in preview in ASP.NET Core 7 and not officially supported until ASP.NET Core 8 or later.

`QuickGrid` sample site: https://aspnet.github.io/quickgridsamples/

# Installing
```posh
dotnet add package microsoft.aspnetcore.components.quickgrid --prerelease
```

# Using
```html
@page "/quickgrid-example"
@using Microsoft.AspNetCore.Components.QuickGrid

<QuickGrid Items="@people">
    <PropertyColumn Property="@(p => p.PersonId)" Sortable="true" />
    <PropertyColumn Property="@(p => p.Name)" Sortable="true" />
    <PropertyColumn Property="@(p => p.PromotionDate)" Format="yyyy-MM-dd" Sortable="true" />
</QuickGrid>
```
```cs
@code {
    private record Person(int PersonId, string Name, DateOnly PromotionDate);

    private IQueryable<Person> people = new[]
    {
        new Person(10895, "Jean Martin", new DateOnly(1985, 3, 16)),
        new Person(10944, "António Langa", new DateOnly(1991, 12, 1)),
        new Person(11203, "Julie Smith", new DateOnly(1958, 10, 10)),
        new Person(11205, "Nur Sari", new DateOnly(1922, 4, 27)),
        new Person(11898, "Jose Hernandez", new DateOnly(2011, 5, 3)),
        new Person(12130, "Kenji Sato", new DateOnly(2004, 1, 9)),
    }.AsQueryable();
}
```