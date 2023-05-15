---
title: "notes > asp.net > blazor > application state"
date: 2023-01-01T00:00:00-06:00
draft: true
---

# Overview
Application state for the current-running instance of the application can be saved and shared between Components.

Create some class to store state:
```cs
public class ApplicationState
{
    // create a property/field for each piece of data to be stored
    public int NumberOfMessages { get; set; } = 0;
}
```

Add the instance to DI:
```cs
builder.Services.AddScoped<ApplicationState>();
```

Inject it and use it:
```cs
[Inject]
public ApplicationState? ApplicationState { get; set; }

int a = ApplicationState.NumberOfMessages;