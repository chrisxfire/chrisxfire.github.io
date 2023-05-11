# Overview
Blazor contains built-in Components for forms.

# EditForm
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

Through EditContext, Blazor checks which fields inside the form have been edited or which validation errors have occurred.

# Input Components
Wrappers around existing HTML inputs.  Inherit from `InputBase`.  Include basic validation:
- InputText
- InputTextArea (multi-line)
- InputNumber
- InputSelect (dropdown)
- InputDate (date picker)
- InputCheckbox
- InputRadio
- InputRadioGroup (group of number of InputRadio Components; allow only one in the group to be selected)
- InputFile (file picker)

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
OnValidSubmit triggers an event handler when a validated form is submitted.  
OnInvalidSubmit triggers if a form is submitted with invalid fields.  
OnSubmit is used whether the form data is invalid or not.  

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