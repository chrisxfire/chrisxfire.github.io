---
title: validation
date: 2023-07-18T00:00:00-06:00
draft: false
weight: 1
---

# Basic validation
To add basic validation to a form, add the `DataAnnotationsValidator` Component. This enables validation using data annotations applied to the model class. 
Blazor performs two types of validation:
1. *Field validation*—performed when the user tabs out of a field.
2. *Model validation*—performed when the user submits the form.
 
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

# Custom validation logic
An `EditForm` instance uses `EditContext` and `ValidationMessageStore` instances to validate form fields.  To apply custom validation:
1. Declare a `ValidationMessageStore` instance and an `EditForm` instance
2. Create an event handler method
3. Assign the handler to `EditContext`'s `OnValidationRequested` event
4. Perform custom validation logic in the event handler
5. Update the `ValidationMessageStore` with the validation error message
<details>
<summary>Example</summary>  

`ExampleForm.razor`  
```html
@page "/form-example-4"
@using Microsoft.Extensions.Logging
@implements IDisposable
@inject ILogger<FormExample4> Logger

<h2>Ship Holodecks</h2>

<EditForm EditContext="editContext" OnValidSubmit="@HandleValidSubmit">
    <label>
        Type 1:
        <InputCheckbox @bind-Value="holodeck.Type1" />
    </label>

    <label>
        Type 2:
        <InputCheckbox @bind-Value="holodeck.Type2" />
    </label>

    <button type="submit">Update</button>

    <ValidationMessage For="() => holodeck.Options" />

    <p>
        <a href="http://www.startrek.com/">Star Trek</a>,
        ©1966-2019 CBS Studios, Inc. and
        <a href="https://www.paramount.com">Paramount Pictures</a>
    </p>
</EditForm>
```
```cs
@code {
    // STEP #1
    private EditContext? editContext;
    private Holodeck holodeck = new();
    // STEP #1
    private ValidationMessageStore? messageStore;

    protected override void OnInitialized()
    {
        editContext = new(holodeck);
        // STEP 3
        editContext.OnValidationRequested += HandleValidationRequested;
        messageStore = new(editContext);
    }

    // STEP #2
    private void HandleValidationRequested(object? sender, 
        ValidationRequestedEventArgs args)
    {
        messageStore?.Clear();

        // STEP 4
        if (!holodeck.Options)
        {
            // STEP 5
            messageStore?.Add(() => holodeck.Options, "Select at least one.");
        }
    }

    private void HandleValidSubmit()
    {
        Logger.LogInformation("HandleValidSubmit called: Processing the form");

        // Process the form
    }

    public class Holodeck
    {
        public bool Type1 { get; set; }
        public bool Type2 { get; set; }
        public bool Options => Type1 || Type2;
    }

    public void Dispose()
    {
        if (editContext is not null)
        {
            editContext.OnValidationRequested -= HandleValidationRequested;
        }
    }
}
```
</details>
<br />

# [Custom Validator components](https://learn.microsoft.com/en-us/aspnet/core/blazor/forms-and-input-components?view=aspnetcore-7.0#validator-components)
Use a custom validator component in cases where an independent model class is used across several components.  

You can create custom validator components to process validation messages for different forms on the same page or the same form at different steps of form processing (for example, client-side validation followed by server-side validation):
```cs
using Microsoft.AspNetCore.Components;
using Microsoft.AspNetCore.Components.Forms;

namespace BlazorSample;

// 1. Derive your validator component from ComponentBase:
public class CustomValidation : ComponentBase
{
    // 2. Create a ValidationMessageStore to hold the current list of form errors:
    private ValidationMessageStore? messageStore;

    // 3. Create the form's EditContext as a CascadingParameter:
    [CascadingParameter]
    private EditContext? CurrentEditContext { get; set; }

    protected override void OnInitialized()
    {
        if (CurrentEditContext is null)
        {
            throw new InvalidOperationException(
                $"{nameof(CustomValidation)} requires a cascading " +
                $"parameter of type {nameof(EditContext)}. " +
                $"For example, you can use {nameof(CustomValidation)} " +
                $"inside an {nameof(EditForm)}.");
        }

        messageStore = new(CurrentEditContext);

        CurrentEditContext.OnValidationRequested += (s, e) => 
            messageStore?.Clear();
        CurrentEditContext.OnFieldChanged += (s, e) => 
            messageStore?.Clear(e.FieldIdentifier);
    }

    // 4. This method is called by the form's component.  Errors are passed in via a Dictionary;
    //    the key is the name of the form field with the error, the value is the error list:
    public void DisplayErrors(Dictionary<string, List<string>> errors)
    {
        if (CurrentEditContext is not null)
        {
            foreach (var err in errors)
            {
                messageStore?.Add(CurrentEditContext.Field(err.Key), err.Value);
            }

            CurrentEditContext.NotifyValidationStateChanged();
        }
    }

    // 5. This clears the ValidationMessageStore and is called:
    //    - Validation is requested (OnValidRequested event is raised)
    //    - A field changes (the OnFieldChanges event is raised)
    //    - Manually be developer code
    public void ClearErrors()
    {
        messageStore?.Clear();
        CurrentEditContext?.NotifyValidationStateChanged();
    }
}
```
The custom validator component is used like this:
```html
<EditForm Model="@starship" OnValidSubmit="@HandleValidSubmit">
    <CustomValidation @ref="customValidation" />
    <ValidationSummary />
```

# Server-side validation with a custom validator component
See: https://learn.microsoft.com/en-us/aspnet/core/blazor/forms-and-input-components?view=aspnetcore-7.0#server-validation-with-a-validator-component

# ValidationSummary and ValidationMessage components
`ValidationSummary` summaries all validation message.  Optionally, output only validation message for a specific model with the `Model` parameter:
```html
<ValidationSummary Model="@starship" />
```

`ValidationMessage<TValue>` displays validation messages for specific field with the `For` attribute and a lambda expression for the model property:
```html
<ValidationMessage For="@(() => starship.MaximumAccommodation)" />
```

Both `ValidationSummary` and `ValidationMessage` support arbitrary attributes which are added to the generated `<div>` or `<ul>` elements.

`ValidationSummary` and `ValidationMessage` can be styled via the validation-message CSS class:
```css
.validation-message {
    color: red;
}
```

# Custom validation attributes
See: https://learn.microsoft.com/en-us/aspnet/core/blazor/forms-and-input-components?view=aspnetcore-7.0#custom-validation-attributes

# Custom validation CSS class attributes
See: https://learn.microsoft.com/en-us/aspnet/core/blazor/forms-and-input-components?view=aspnetcore-7.0#custom-validation-css-class-attributes

# Validating nested models, collections, and complex types
See: https://learn.microsoft.com/en-us/aspnet/core/blazor/forms-and-input-components?view=aspnetcore-7.0#nested-models-collection-types-and-complex-types

