---
title: input components
date: 2023-07-18T00:00:00-06:00
draft: false
weight: 1
---

# input components
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

# error message template support
`InputDate` and `InputNumber` both support error message templates to provide a custom error message:
```html
<label>
    Production Date:
    <InputDate @bind-Value="starship.ProductionDate" 
               DisplayName="Production Date" 
               ParsingErrorMessage="The {0} field has an incorrect date value." />
</label>
```

# [InputText](https://learn.microsoft.com/en-us/aspnet/core/blazor/forms-and-input-components?view=aspnetcore-7.0#inputtext-based-on-the-input-event)
```html
<EditForm Model="@Employee">
    <!-- 2-way data binding with @bind-value: -->
    <InputText id="lastName" @bind-value="@Employee.LastName" placeholder="Enter last name"></InputText>
</EditForm>
```

## Using HTML's oninput event with `InputText`
Create a custom component based on `InputText`.  

Assuming this model:
`ExampleModel.cs`
```cs
using System.ComponentModel.DataAnnotations;

public class ExampleModel
{
    [Required]
    [StringLength(10, ErrorMessage = "Name is too long.")]
    public string? Name { get; set; }
}
```

Inherit the InputText component and set the event binding to the 'oninput' event:
`Shared/CustomInputText.razor`
```html {hl_lines=[1,6]}
@inherits InputText

<input @attributes="AdditionalAttributes" 
       class="@CssClass" 
       @bind="CurrentValueAsString" 
       @bind:event="oninput" />
```

Use the component:
```html {hl_lines=9}
@page "/form-example-7"
@using Microsoft.Extensions.Logging
@inject ILogger<FormExample7> Logger

<EditForm Model="@exampleModel" OnValidSubmit="@HandleValidSubmit">
    <DataAnnotationsValidator />
    <ValidationSummary />

    <CustomInputText @bind-Value="exampleModel.Name" />

    <button type="submit">Submit</button>
</EditForm>

<p>
    CurrentValue: @exampleModel.Name
</p>
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

# [InputSelect](https://learn.microsoft.com/en-us/aspnet/core/blazor/forms-and-input-components?view=aspnetcore-7.0#multiple-option-selection-with-the-inputselect-component)
```html
<InputSelect id="country" class=form-control col-sm-8" @bind-value="@Employee.CountryId">
    @foreach (var country in Countries)
    {
        <option value="@country.CountryId">@country.Name</option>
    }
</InputSelect>
```

## Multi-Option Selection with `InputSelect`
Bind multiple options by setting the `@bind-value` to an array type. Doing so also makes the HTML `multiple` attribute optional:
```html
            <!-- starship.SelectedClassification is an array type: -->
            <InputSelect @bind-Value="starship.SelectedClassification">
                <option value="@Classification.Exploration">Exploration</option>
                <option value="@Classification.Diplomacy">Diplomacy</option>
                <option value="@Classification.Defense">Defense</option>
                <option value="@Classification.Research">Research</option>
            </InputSelect>
```

The `@onchange` event provides an array of the selected options via event arguments (`ChangeEventArgs`).

# radio buttons
See: https://learn.microsoft.com/en-us/aspnet/core/blazor/forms-and-input-components?view=aspnetcore-7.0#radio-buttons

