# Overview
Blazor contains built-in Components for forms.

# EditForm
The Blazor version of HTML's form.
```cshtml
<EditForm Model="@Employee">
</EditForm>

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
```cshtml
<EditForm Model="@Employee">
    <!-- 2-way data binding with @bind-value: -->
    <InputText id="lastName" @bind-value="@Employee.LastName" placeholder="Enter last name">
    </InputText>
</EditForm>
```

## InputSelect