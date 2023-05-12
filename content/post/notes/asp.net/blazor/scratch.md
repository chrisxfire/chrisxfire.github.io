# Data Binding
## One-way Data Binding
Used to display data:
```html
<h1 class="page-title">
    Details for @FirstName @LastName
</h1>
```
```cs
@code 
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
}
```

Or in a form control, such as an input:
```html
<!-- changing the value of the input, changing the value in the UI will not change it in the Employee instance -->
<input type="text" class="form-control-plaintext">
    @Employee.Firstname
<input>
```
```cs
@code
{
    public Employee Employee { get; set; }
}
```

## Two-way Data Binding
The most common form of data binding.  Usually used in conjunction with forms.  
If the user changes the value, it will be updated on the property (by default, when they select out of the input).
Uses the `@bind` directive.

Example
```html
<!-- @bind specifies that we should bind the Employee.LastName to this Component: -->
<input id="lastName" @bind="@Employee.LastName" placeholder="Enter last name" />
```

### Using `bind-Value` and `bind-value-event`
```html
<!-- property value will be updated every time user types a character: -->
<input id="lastName" 
    @bind-Value="Employee.LastName" 
    @bind-Value:event="oninput"
    placeholder="Enter last name" />
```