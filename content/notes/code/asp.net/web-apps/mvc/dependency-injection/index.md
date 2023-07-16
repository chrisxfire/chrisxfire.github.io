---
title: notes > code > asp.net > web apps > mvc > dependency injection
date: 2023-03-22T00:00:00-06:00
draft: false
weight: 1
---

# Dependency Injection into Controllers
Code sample: [View or download sample code (github.com)](https://github.com/dotnet/AspNetCore.Docs/tree/main/aspnetcore/mvc/controllers/dependency-injection/sample)

MVC controllers request dependencies explicitly via constructors.
Assuming an `IDateTime` service:
```cs
public class HomeController : Controller
{
    private readonly IDateTime _dateTime;

    public HomeController(IDateTime dateTime) =>
        _dateTime = dateTime;
    
    …
}
```

# Dependency Injection into Actions
Use the `[FromServices]` attribute:
```cs
public IActionResult About([FromServices] IDateTime dateTime) =>
    Content( $"Current server time: {dateTime.Now}");
```

# [Options Pattern to Access Settings](https://learn.microsoft.com/en-us/aspnet/core/mvc/controllers/dependency-injection?view=aspnetcore-7.0#access-settings-from-a-controller)

# Dependency Injection into Views
Displaying a configuration value in a Razor Pages view:
```html
@page
@model PrivacyModel <-- 
@using Microsoft.Extensions.Configuration <--
@inject IConfiguration Configuration
@{
    ViewData["Title"] = "Privacy RP";
}
<h1>@ViewData["Title"]</h1>

<p>PR Privacy</p>

<h2>
   MyRoot:MyParent:MyChildName: @Configuration["MyRoot:MyParent:MyChildName"] <--
</h2>
```

Displaying a configuration item in a MVC view:
```html
@using Microsoft.Extensions.Configuration <--
@inject IConfiguration Configuration <--
@{
    ViewData["Title"] = "Privacy MVC";
}
<h1>@ViewData["Title"]</h1>

<p>MVC Use this page to detail your site's privacy policy.</p>

<h2>
   MyRoot:MyParent:MyChildName: @Configuration["MyRoot:MyParent:MyChildName"] <--
</h2>
```

Injecting a service in an MVC view:
```html
@using System.Threading.Tasks
@using ViewInjectSample.Model
@using ViewInjectSample.Model.Services
@model IEnumerable<ToDoItem> <--
@inject StatisticsService StatsService <--
<!DOCTYPE html>
<html>
<head>
    <title>To Do Items</title>
</head>
<body>
    <div>
        <h1>To Do Items</h1>
        <ul>
            <li>Total Items: @StatsService.GetCount()</li> <--
            <li>Completed: @StatsService.GetCompletedCount()</li> <--
            <li>Avg. Priority: @StatsService.GetAveragePriority()</li> <--
        </ul>
        <table>
            <tr>
                <th>Name</th>
                <th>Priority</th>
                <th>Is Done?</th>
            </tr>
            @foreach (var item in Model)
            {
                <tr>
                    <td>@item.Name</td>
                    <td>@item.Priority</td>
                    <td>@item.IsDone</td>
                </tr>
            }
        </table>
    </div>
</body>
</html>
```
## Example
Consider a user profile form that includes options for specifying gender, state, and other preferences.  Inject services directly into the view to obtain the options.

The service provides just the data need for the form:
```cs
namespace ViewInjectSample.Model.Services;

public class ProfileOptionsService
{
    public List<string> ListGenders() =>
        new List<string>() {"Female", "Male"};

    public List<State> ListStates()
    {
        // Add a few states
        return new List<State>()
        {
            new State("Alabama", "AL"),
            new State("Alaska", "AK"),
            new State("Ohio", "OH")
        };
    }

    public List<string> ListColors() =>
        new List<string>() { "Blue","Green","Red","Yellow" };
}
```
The controller action to display a profile editing form only needs to pass the form the profile instance:
```cs
using Microsoft.AspNetCore.Mvc;
using ViewInjectSample.Model;

namespace ViewInjectSample.Controllers;

public class ProfileController : Controller
{
    public IActionResult Index()
    {
        // A real app would up profile based on the user.
        var profile = new Profile()
        {
            Name = "Rick",
            FavColor = "Blue",
            Gender = "Male",
            State = new State("Ohio","OH")
        };

        return View(profile);
    }
}
```
The list is populated by the service injected into the view:
```html
@using System.Threading.Tasks
@using ViewInjectSample.Model.Services
@model ViewInjectSample.Model.Profile
@inject ProfileOptionsService Options
<!DOCTYPE html>
<html>
<head>
    <title>Update Profile</title>
</head>
<body>
<div>
    <h1>Update Profile</h1>
    Name: @Html.TextBoxFor(m => m.Name)
    <br/>
    Gender: @Html.DropDownList("Gender",
           Options.ListGenders().Select(g => 
                new SelectListItem() { Text = g, Value = g }))
    <br/>

    State: @Html.DropDownListFor(m => m.State!.Code,
           Options.ListStates().Select(s => 
                new SelectListItem() { Text = s.Name, Value = s.Code}))
    <br />

    Fav. Color: @Html.DropDownList("FavColor",
           Options.ListColors().Select(c => 
                new SelectListItem() { Text = c, Value = c }))
    </div>
</body>
</html>
```
