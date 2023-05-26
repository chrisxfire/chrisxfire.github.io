---
title: "notes > asp.net > web apps > blazor > fundamentals > components > forms"
date: 2023-04-01T00:00:00-06:00
draft: false
---

# Overview
Blazor contains built-in Components for forms.

# `EditForm`
The Blazor version of HTML's form.
```html
<EditForm Model="@Employee">
</EditForm>
```
```cs
@code
{
    public Employee Employee { get; set; } = new Employee();
}
```

Through `EditContext`, Blazor checks which fields inside the form have been edited or which validation errors have occurred.

# Input Components
Wrappers around existing HTML inputs.  Inherit from `InputBase`.  Include basic validation:
- `InputText`
- `InputTextArea` (multi-line)
- `InputNumber`
- `InputSelect` (dropdown)
- `InputDate` (date picker)
- `InputCheckbox`
- `InputRadio`
- `InputRadioGroup` (group of number of `InputRadio` Components; allow only one in the group to be selected)
- `InputFile` (file picker)

## InputText
```html
<EditForm Model="@Employee">
    <!-- 2-way data binding with @bind-value: -->
    <InputText id="lastName" @bind-value="@Employee.LastName" placeholder="Enter last name"></InputText>
</EditForm>
```

## InputSelect
```html
<InputSelect id="country" class=form-control col-sm-8" @bind-value="@Employee.CountryId">
    @foreach (var country in Countries)
    {
        <option value="@country.CountryId">@country.Name</option>
    }
</InputSelect>
```

# Event Handlers for Submitting Forms
`OnValidSubmit` triggers an event handler when a validated form is submitted.    
`OnInvalidSubmit` triggers if a form is submitted with invalid fields.  
`OnSubmit` is used whether the form data is invalid or not.  

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
```html
<EditForm Model="@Employee"
    OnValidSubmit="@HandleValidSubmit"
    OnInvalidSubmit="@HandleInvalidSubmit"
    ...
    <DataAnnotationsValidator />
    <ValidationSummary />
</EditForm>
```

To display validation errors next to the violating Component, add the `ValidationMessage` Component:
```html
...
<div class="col-md-8">
    <InputText id="lastName" @bind-Value="@Employee.LastName" ...>
</div>
<ValidationMessage class="offset-md-3 col-md-8" For="@(() => Employee.LastName)" />
...
```