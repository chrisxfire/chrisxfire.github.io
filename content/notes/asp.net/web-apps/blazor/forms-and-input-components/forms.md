---
title: forms
date: 2023-04-01T00:00:00-06:00
draft: true
weight: 1
---

# overview
Blazor contains built-in Components for forms.  `Microsoft.AspNetCore.Components.Forms` contains classes for managing forms and access to built-in `Input*` components.  This namespace is included in `_Imports.razor` by default.

# `EditForm`
The Blazor version of HTML's form.

`ExampleModel.cs`
```cs
public class ExampleModel
{
    public string? Name { get; set; }
}
```

`Pages/FormExample1.razor`
```html
@page "/form-example-1"
@using Microsoft.Extensions.Logging
@inject ILogger<FormExample1> Logger

<!-- The Component is rendered here. OnSubmit is a callback and registers HandleSubmit as the handler: -->
<EditForm Model="@exampleModel" OnSubmit="@HandleSubmit">
    <!-- the InputText Component's @bind-Value directive attribute binds example.Model.Name to InputText's Value property: -->
    <InputText id="name" @bind-Value="exampleModel.Name" />

    <button type="submit">Submit</button>
</EditForm>
```
```cs
@code {
    // This field is assigned to EditForm.Model above
    private ExampleModel exampleModel = new();

    private void HandleSubmit()
    {
        Logger.LogInformation("HandleSubmit called");

        // Process the form
    }
}
```

# binding a form
An `EditForm` creates an `EditContext` based on the assigned model instance and makes it available as a cascading value to other Components in the same form. You can bind a form to data by assigning to `EditForm.Model`...
```html
<EditForm Model="@exampleModel" ...>
```
```cs
@code {
    private ExampleModel exampleModel = new() { ... };
}
```
...or `EditForm.EditContext`...
```html
<EditForm EditContext="@editContext" ...>
```
```cs
@code {
    private ExampleModel exampleModel = new() { ... };
    private EditContext? editContext;

    protected override void OnInitialized()
    {
        editContext = new(exampleModel);
    }
}
```
...but don't do both.

Note that `EditContext` **cannot** be changed after it is assigned a value.

# display name support
Several Components support display names with the `InputBase<TValue>.DisplayName` parameter:
```html
<label>
    Production Date:
    <InputDate @bind-Value="starship.ProductionDate" 
               DisplayName="Production Date" />
</label>
```
Without setting the `DisplayName` property, a validation's error message would display this error: `The ProductionDate field must be a date.`  
With it set, it displays this error: `The Production Date field must be a date.`

# event handlers for submitting forms
- `OnValidSubmit` triggers an event handler when a validated form is submitted.    
- `OnInvalidSubmit` triggers if a form is submitted with invalid fields.  
- `OnSubmit` is used whether the form data is invalid or not.  The form is validated by calling `EditContext.Validate` in the event handler.  If `Validate` returns `true`, the form is valid.

## example
```html
<EditForm Model="@Employee"
    OnValidSubmit="@HandleValidSubmit"
    OnInvalidSubmit="@HandleInvalidSubmit"
    <InputText id="lastName" @bind-Value="@Employee.LastName" placeholder="Enter last name">
    </InputText>
    <button type="submit">Save employee</button>
</EditForm>
```
