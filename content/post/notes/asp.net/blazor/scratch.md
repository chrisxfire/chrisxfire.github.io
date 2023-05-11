# Data Binding
## One-way Data Binding
Used to display data:
```razor
<h1 class="page-title">
    Details for @FirstName @LastName
</h1>

@code 
{
    public string FirstName { get; set; }
    public string LastName { get; set; }
}
```

Or in a form control, such as an input:
```razor
<!-- changing the value of the input, changing the value in the UI will not change it in the Employee instance -->
<input type="text" class="form-control-plaintext">
    @Employee.Firstname
<input>

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
```razor
<!-- @bind specifies that we should bind the Employee.LastName to this Component: -->
<input id="lastName" @bind="@Employee.LastName" placeholder="Enter last name" />
```

### Using `bind-value` and `bind-value-event`
```razor
<input id="lastName" 
    @bind-value="Employee.LastName" 
    <!-- property value will be updated every time user types a character: -->
    @bind-value:event="oninput"
    placeholder="Enter last name" />
```