---
title: notes > code > asp.net > web apps > blazor > components > forms
date: 2023-04-01T00:00:00-06:00
draft: false
---

# Overview
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

# Binding a Form
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

# Input Components
Wrappers around existing HTML inputs.  Inherit from `InputBase`.  Include basic validation:
- `InputCheckbox`
- `InputDate` (date picker)
  - Registers unparseable values as validation errors
- `InputFile` (file picker) (see [ASP.NET Core Blazor file uploads](https://learn.microsoft.com/en-us/aspnet/core/blazor/file-uploads?view=aspnetcore-7.0))
- `InputNumber`
  - Registers unparseable values as validation errors
- `InputSelect` (dropdown)
- `InputRadio`
- `InputRadioGroup` (group of number of `InputRadio` Components; allow only one in the group to be selected)
- `InputText`
- `InputTextArea` (multi-line)

## [InputText](https://learn.microsoft.com/en-us/aspnet/core/blazor/forms-and-input-components?view=aspnetcore-7.0#inputtext-based-on-the-input-event)
```html
<EditForm Model="@Employee">
    <!-- 2-way data binding with @bind-value: -->
    <InputText id="lastName" @bind-value="@Employee.LastName" placeholder="Enter last name"></InputText>
</EditForm>
```

## [InputSelect](https://learn.microsoft.com/en-us/aspnet/core/blazor/forms-and-input-components?view=aspnetcore-7.0#multiple-option-selection-with-the-inputselect-component)
```html
<InputSelect id="country" class=form-control col-sm-8" @bind-value="@Employee.CountryId">
    @foreach (var country in Countries)
    {
        <option value="@country.CountryId">@country.Name</option>
    }
</InputSelect>
```

## Radio Buttons
See: https://learn.microsoft.com/en-us/aspnet/core/blazor/forms-and-input-components?view=aspnetcore-7.0#radio-buttons

# Display name support
See: https://learn.microsoft.com/en-us/aspnet/core/blazor/forms-and-input-components?view=aspnetcore-7.0#display-name-support

# Error message template support
See: https://learn.microsoft.com/en-us/aspnet/core/blazor/forms-and-input-components?view=aspnetcore-7.0#error-message-template-support

# Event Handlers for Submitting Forms
`OnValidSubmit` triggers an event handler when a validated form is submitted.    
`OnInvalidSubmit` triggers if a form is submitted with invalid fields.  
`OnSubmit` is used whether the form data is invalid or not.  The form is validated by calling `EditContext.Validate` in the event handler.  If `Validate` returns `true`, the form is valid.

## Example
```html
<EditForm Model="@Employee"
    OnValidSubmit="@HandleValidSubmit"
    OnInvalidSubmit="@HandleInvalidSubmit"
    <InputText id="lastName" @bind-Value="@Employee.LastName" placeholder="Enter last name">
    </InputText>
    <button type="submit">Save employee</button>
</EditForm>
```

# Validation
To add validation to a form, add the `DataAnnotationsValidator` Component. This enables validation using data annotations applied to the model class.  
To display validation errors at the top of the page, add the `ValidationSummary` Component.
`Pages/FormExample2.razor`
```html
@page "/form-example-1"
@using Microsoft.Extensions.Logging
@inject ILogger<FormExample1> Logger
<!-- OnValidSubmit only invokes the assigned event handler if the form is valid when submitted:-->
<EditForm Model="@exampleModel" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <InputText id="name" @bind-Value="exampleModel.Name" />

    <button type="submit">Submit</button>
</EditForm>
```
```cs
@code {
    private ExampleModel exampleModel = new();

    private void HandleValidSubmit()
    {
        Logger.LogInformation("HandleValidSubmit called");

        // Process the valid form
    }
}
```
