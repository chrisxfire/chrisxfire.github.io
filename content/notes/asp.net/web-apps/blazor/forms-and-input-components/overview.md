---
title: overview
date: 2025-01-10T00:00:00-06:00
draft: false
weight: -1
tags:
 - kb/asp.net/blazor/forms
 - kb/asp.net/blazor/input-components
---

# [overview](https://learn.microsoft.com/en-us/aspnet/core/blazor/forms/?view=aspnetcore-9.0&preserve-view=true)
> [!IMPORTANT]
> Availability: ASP.NET 9

The Blazor framework supports standard HTML forms via the `<form>` tag and `EditForm` and other components via the `Microsoft.AspNetCore.Components.Forms` namespace.

## HTML form example
Create a form with the `<form>` tag and specify an `@onsubmit` handler for handling the submitted form request:
`StarshipPlainForm.razor`
```html
@page "/starship-plain-form"
@inject ILogger<StarshipPlainForm> Logger

<!-- 
 The form will be rendered here. 
 The Submit method is registered as a handler for the @onsubmit callback.
 The @formname token uniquely identifies the form to the Blazor framework: 
-->
<form method="post" @onsubmit="Submit" @formname="starship-plain-form">
    <AntiforgeryToken />
    <div>
        <label>
            Identifier: 
            <!-- Binds the Model.Id property to the InputText component's Value property: -->
            <InputText @bind-Value="Model!.Id" />
        </label>
    </div>
    <div>
        <button type="submit">Submit</button>
    </div>
</form>
```
```cs
@code {
    // This attribute indicates the Model property will be supplied from the form data. Data in the request that matches
    // the name of this property is bound to it.
    [SupplyParameterFromForm]
    private Starship? Model { get; set; }

    protected override void OnInitialized() => Model ??= new();

    private void Submit() => Logger.LogInformation("Id = {Id}", Model?.Id);

    public class Starship
    {
        public string? Id { get; set; }
    }
}
```

## antiforgery
When `AddRazorComponents` is called in `Program`, antiforgery services are added.

Antiforgery middleware is enabled by calling `UseAntiforgery` in the request processing pipeline. This call must be made in a specific sequence in relation to other middleware calls. It must be called:
- After
    - `UseRouting`
    - `UseAuthentication`
    - `UseAuthorization`
- Between
    - `UseRouting` and `UseEndpoints`

The `AntiForgeryToken` component renders an antiforgery token in a hidden field. The `[RequireAntiforgeryToken]` attribute enables antiforgery protection.

For HTML forms, manually add the AntiforgeryToken component to the form:
```html
<form method="post" @onsubmit="Submit" @formname="starshipForm">
    <AntiforgeryToken />
    <input id="send" type="submit" value="Send" />
</form>

@if (submitted)
{
    <p>Form submitted!</p>
}
```
```cs
@code{
    private bool submitted = false;

    private void Submit() => submitted = true;
}
```

## `EditForm`
### `EditForm` component example
`Starship1`
```html
@page "/starship-1"
@inject ILogger<Starship1> Logger

<!-- 
 The EditForm component is rendered here.
 The Submit method is registered as a handler for the @onsubmit callback.
 The FormName property uniquely identifies the form to the Blazor framework: -->
<EditForm Model="Model" OnSubmit="Submit" FormName="Starship1">
    <div>
        <label>
            Identifier:
            <InputText @bind-Value="Model!.Id" />
        </label>
    </div>
    <div>
        <button type="submit">Submit</button>
    </div>
</EditForm>
```
```cs
@code {
    // This attribute indicates the Model property will be supplied from the form data. Data in the request that matches
    // the name of this property is bound to it.
    [SupplyParameterFromForm]
    private Starship? Model { get; set; }

    protected override void OnInitialized() => Model ??= new();

    private void Submit() => Logger.LogInformation("Id = {Id}", Model?.Id);

    public class Starship
    {
        public string? Id { get; set; }
    }
}
```

### extended `EditForm` example
```html
@page "/starship-2"
<!-- Enables the use of the DataAnnotationsValidator component: -->
@using System.ComponentModel.DataAnnotations
@inject ILogger<Starship2> Logger

<!-- The OnValidSubmit property processes the attached event handler only if the form is valid when submitted: -->
<EditForm Model="Model" OnValidSubmit="Submit" FormName="Starship2">
    <!-- This component adds validation support using data annotations: -->
    <DataAnnotationsValidator />
    <!-- This component displays validation messages when the form is invalid on submit: -->
    <ValidationSummary />
    <label>
        Identifier: 
        <InputText @bind-Value="Model!.Id" />
    </label>
    <button type="submit">Submit</button>
</EditForm>
```
```cs
@code {
    [SupplyParameterFromForm]
    private Starship? Model { get; set; }

    protected override void OnInitialized() => Model ??= new();

    private void Submit() => Logger.LogInformation("Id = {Id}", Model?.Id);

    public class Starship
    {
        // The Required attribute ensures that the <input> form field is not blank when submitted:
        [Required]
        // This attribute ensures the <input> form field contains a value of at least 10 characters:
        [StringLength(10, ErrorMessage = "Id is too long.")]
        public string? Id { get; set; }
    }
}
```

### handling form submission with `EditForm`
`EditForm` provides these callbacks for handling form submission:
- Use `OnValidSubmit` to assign an event handler to run when a form with valid fields is submitted.
- Use `OnInvalidSubmit` to assign an event handler to run when a form with invalid fields is submitted.
- Use `OnSubmit` to assign an event handler to run regardless of the form's validation status.

### clearing a form
> [!NOTE]
> StateHasChanged is called implicitly by the Blazor framework after an event handler is invoked, so there's no need to call it in these examples.

Reset a form by clearing its model back to its default state:
```html
<button @onclick="ClearForm">Clear form</button>

...
```
```cs
private void ClearForm() => Model = new();
```

Or, use an explicit razor expression:
```html
<button @onclick="@(() => Model = new())">Clear form</button>
```

### clearing a field
> [!NOTE]
> StateHasChanged is called implicitly by the Blazor framework after an event handler is invoked, so there's no need to call it in these examples.

Reset a field by clearing its model back to its default state:
```html
<button @onclick="ResetId">Reset Identifier</button>

...
```
```cs
private void ResetId() => Model!.Id = string.Empty;
```

Or, use an explicit razor expression:
```html
<button @onclick="@(() => Model!.Id = string.Empty)">Reset Identifier</button>
```

## enhanced navigation
Enhanced navigation for form POST requests can be enabled...
<!-- TODO: link to enhanced navigation note -->

...in `EditForm` forms via the `Enhance` parameter:
```html
<EditForm ... Enhance ...>
    ...
</EditForm>
```

...in HTML forms via the `data-enhance` attribute:
```html
<form ... data-enhance ...>
    ...
</form>
```

A form's ancestor element <r>cannot</r> be set with enhanced navigation to enable enhanced form handling:
```html
<div ... data-enhance ...>
    <form ...>
        <!-- NOT enhanced -->
    </form>
</div>
```

> [!CAUTION]
> Blazor's enhanced navigation and form handling may undo dynamic changes to the DOM if the updated content is not part of the server rendering. 

To preserve the content, use the `data-permanent` attribute:
```html
<div data-permanent>
    ...
</div>
```