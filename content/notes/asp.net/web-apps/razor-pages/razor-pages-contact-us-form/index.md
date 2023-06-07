---
title: notes > asp.net > web apps > razor pages > razor pages contact us form
date: 2023-04-19T00:00:00-06:00
draft: false
---

# Overview
In `Program.cs`:
```cs
builder.Services.AddDbContext<CustomerDbContext>(options =>
    options.UseInMemoryDatabase("name"));
```

## The data model
```cs
using System.ComponentModel.DataAnnotations;

namespace RazorPagesContacts.Models
{
    public class Customer
    {
        public int Id { get; set; }

        [Required, StringLength(10)]
        public string? Name { get; set; }
    }
}
```

## The database context
```cs
using Microsoft.EntityFrameworkCore;

namespace RazorPagesContacts.Data
{
    public class CustomerDbContext : DbContext
    {
        public CustomerDbContext (DbContextOptions<CustomerDbContext> options)
            : base(options)
        {
        }

        public DbSet<RazorPagesContacts.Models.Customer> Customer => Set<RazorPagesContacts.Models.Customer>();
    }
}
```

## The view
`Pages/Customers/Create.cshtml`
```html
@page
@model RazorPagesContacts.Pages.Customers.CreateModel
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<p>Enter a customer name:</p>

<form method="post">
    Name:
    <input asp-for="Customer!.Name" />
    <input type="submit" />
</form>
```

## The page model
Separates the logic of a page from its presentation.  It defines page handlers for requests sent to the page.

`Pages/Customers/Create.cshtml.cs`
```cs
public class CreateModel : PageModel
{
    private readonly Data.CustomerDbContext _context;

    public CreateModel(Data.CustomerDbContext context)
    {
        _context = context;
    }

    public IActionResult OnGet()
    {
        return Page(); // this displays the CreateModel.cshtml Razor Page
    }

    // Binding to properties removes the need to convert HTTP data to the model type.
    [BindProperty] // Razor Pages, by default, only binds properties with non-GET verbs.  
    public Customer? Customer { get; set; }

    public async Task<IActionResult> OnPostAsync() // this is a handler method (similar to a controller)
    {
	   // check for errors
        if (!ModelState.IsValid)
        {
            return Page(); // if there are errors, call the Page helper method, which returns an instance of PageResult
        }

        if (Customer != null) _context.Customer.Add(Customer);
	   
	   // no errors: save and redirect back to Index
        await _context.SaveChangesAsync();

	      // RedirectToPage is an action result that returns an instance of RedirectToPageResult
        return RedirectToPage("./Index"); 
    }
}
```

`Pages/Customers/Create.cshtml`
```html
@page
@model RazorPagesContacts.Pages.Customers.CreateModel
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers @* this makes Tag Helpers available *@

<p>Enter a customer name:</p>

<form method="post">
    Name:
    <input asp-for="Customer!.Name" /> <!-- binds the HTML input element to the Customer.Name model expression -->
    <input type="submit" />
</form>
```

## The home page
`Index.cshtml`
```html
@page
@model RazorPagesContacts.Pages.Customers.IndexModel
@addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers

<h1>Contacts home page</h1>
<form method="post">
    <table class="table">
        <thead>
            <tr>
                <th>ID</th>
                <th>Name</th>
                <th></th>
            </tr>
        </thead>
        <tbody>
        @if (Model.Customers != null)
        {
            foreach (var contact in Model.Customers)
            {
                <tr>
                    <td> @contact.Id </td>
                    <td>@contact.Name</td>
                    <td>
                        <!-- <snippet_Edit> -->
				    <!-- This Anchor Tag Helper uses the asp-route-{value} attribute to generate a link to the Edit page.
					    This link contains route data with the contact ID. -->
                        <a asp-page="./Edit" asp-route-id="@contact.Id">Edit</a> |
                        <!-- </snippet_Edit> -->
                        <!-- <snippet_Delete> -->
                        <button 
						type="submit" 
                        <!-- specifies that OnPostDeleteAsync processes this POST request: -->
						asp-page-handler="delete"  
						asp-route-id="@contact.Id">
					delete
					</button>
                        <!-- </snippet_Delete> -->
                    </td>
                </tr>
            }
        }
        </tbody>
    </table>
    <a asp-page="Create">Create New</a>
</form>
```

## The home page's `PageModel`
`Index.cshtml.cs`
```cs
public class IndexModel : PageModel
{
    private readonly Data.CustomerDbContext _context;
    public IndexModel(Data.CustomerDbContext context)
    {
        _context = context;
    }

    public IList<Customer>? Customers { get; set; }

    public async Task OnGetAsync()
    {
        Customers = await _context.Customer.ToListAsync();
    }

    public async Task<IActionResult> OnPostDeleteAsync(int id)
    {
        var contact = await _context.Customer.FindAsync(id);

        if (contact != null)
        {
            _context.Customer.Remove(contact);
            await _context.SaveChangesAsync();
        }

        return RedirectToPage();
    }
}
```

## The Edit File
`Edit.cshtml`
```cs
@page "{id:int}"
@model RazorPagesContacts.Pages.Customers.EditModel

@{
    ViewData["Title"] = "Edit";
}

<h1>Edit</h1>

<h4>Customer</h4>
<hr />
<div class="row">
    <div class="col-md-4">
        <form method="post">
            <div asp-validation-summary="ModelOnly" class="text-danger"></div>
            <input type="hidden" asp-for="Customer!.Id" />
            <div class="form-group">
                <label asp-for="Customer!.Name" class="control-label"></label>
                <input asp-for="Customer!.Name" class="form-control" />
                <span asp-validation-for="Customer!.Name" class="text-danger"></span>
            </div>
            <div class="form-group">
                <input type="submit" value="Save" class="btn btn-primary" />
            </div>
        </form>
    </div>
</div>

<div>
    <a asp-page="./Index">Back to List</a>
</div>

@section Scripts {
    @{await Html.RenderPartialAsync("_ValidationScriptsPartial");}
}
```
