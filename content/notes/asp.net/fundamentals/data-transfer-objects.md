---
title: data transfer objects
date: 2023-09-27T00:00:00-06:00
draft: false
weight: 1
---

# [Overview](https://learn.microsoft.com/en-us/aspnet/core/tutorials/first-web-api?view=aspnetcore-7.0&tabs=visual-studio#prevent-over-posting)  

Data Transfer Objects (DTOs) are a subset of a data model. They are used to limit the data that is input or returned from a web app by using a subset of the model. They are also used to prevent over-posting (aka mass assignment) attacks.

Note: not to be confused with a `Microsoft.AspNetCore.Components.Web.DataTransfer` object.

# Preventing Overposting with DTOs
## Example Overposting Vulnerability
> Reference: https://andrewlock.net/preventing-mass-assignment-or-over-posting-in-asp-net-core/

Consider this model:
```cs
public class UserModel
{
    public string Name { get; set; }
    public bool IsAdmin { get; set; }
}
```

The user can edit the `Name` property. The `IsAdmin` property is used to control the markup they see:
```html
@model UserModel

<form asp-action="Vulnerable" asp-Controller="Home">
    <div class="form-group">
        <label asp-for="Name"></label>
        <input class="form-control" type="TextBox" asp-for="Name" />
    </div>
    <div class="form-group">
        @if (Model.IsAdmin)
        {
            <i>You are an admin</i>
        }
        else
        {
            <i>You are a standard user</i>
        }
    </div>
    <button class="btn btn-sm" type="submit">Submit</button>
</form>
```

Here's the controller action:
```cs
[HttpPost]
public IActionResult Vulnerable(UserModel model)
{
    return View("Index", model);
}
```

In a normal flow, the user can only edit the `Name` field. But the HTML can be manipulated: the `IsAdmin` field can be set to `true` and the model binder will bind that value.

Some ways to defend against such an attack include;
* Using `BindAttribute` on the action method
* Using `[Editable]` or `[BindNever]` on the model
* Using a DTO
* Using `ModelMetadataTypeAttribute`

## Defending Against Overposting with DTOs
With a DTO, a second version of the model is created that only includes a subset of its properties:
```cs
public class UserModel
// Alternatively, UserModel could inherit UserModelDto
{
    public string Name { get; set; }
    public bool IsAdmin { get; set; }
}

public class UserModelDto 
{
    public string Name { get; set; }
}
```

The DTO model is the one provided to the controller action:
```cs
public IActionResult Safe3(UserModelDto userModelDto)
{
    var model = new UserModel();

    model.Name = userModelDto.Name;

    return View("Index", model);
}
```

Now, even if the `IsAdmin` property is posted, it cannot be bound (there is no `IsAdmin` property on `UserModelDto`).