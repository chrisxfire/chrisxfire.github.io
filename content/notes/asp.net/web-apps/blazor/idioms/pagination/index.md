---
title: notes > asp.net > web apps > blazor > idioms > pagination
date: 2023-05-20T00:00:00-06:00
draft: false
---

From Pluralsight/Building a Data-driven ASP.NET Core 6 Blazor Server Application with EF Core

# Overview
Pagination allows you to limit the number of results you return per page and allows the user to request more results by specifying a page number.

## Implement Pagination
Implementing pagination functionality involves:
1. Counting the total number of records the Component has
2. Specifying the number of records to show per page
3. Using the above, counting the total number of pages (pages = records / recordsPerPage)
4. Updating the logic to account for invalid page requests such as 0 or a number greater than the total number of pages
5. Updating the page routes to include a pagination parameter  

`EmployeeOverview.razor`
```html
@* since int is nullable, if no currentPage parameter is specified, this directive will still route to this EmployeeOverview Component: *@
@page "/employees/list/{currentPage:int?}"
@inject IDbContextFactory<EmployeeManagerDbContext> ContextFactory;
@inject NavigationManager NavigationManager; @* NavigateTo() *@

<PageTitle>Employees</PageTitle>
<h1>Employees</h1>

<!-- ... -->
```
```cs
@code
{
    private const int ItemsPerPage = 4;
    // a property to hold the total number of pages:
    private int TotalPages { get; set; }
    private Employee[]? Employees { get; set; }

    // this Parameter is populated from the route:
    [Parameter]
    public int? CurrentPage { get; set; }

    protected override async Task OnParametersSetAsync()
    {
        // if this page was called without paging or with a page value that is <= 0, navigate to /employees/list/1:
        if (CurrentPage is null or < 1)
        {
            NavigationManager.NavigateTo("/employees/list/1");
            return;
        }

        using var context = ContextFactory.CreateDbContext();

        // get the employee count
        var employeeCount = await context.Employees.CountAsync();

        // get the total number of pages we have by dividing the employee count with items per page:
        // Math.Ceiling rounds up to the next whole integer
        TotalPages = employeeCount == 0 ? 1 : (int)Math.Ceiling((double)employeeCount / ItemsPerPage);

        // if the requested page is beyond the total number of pages we have, navigate to the last page that we have:
        if (CurrentPage > TotalPages)
        {
            NavigationManager.NavigateTo($"/employees/list{TotalPages}");
            return;
        }

        // if CurrentPage == 1, itemsToSkip == 0
        // if CurrentPage == 2, itemsToSkip == 4
        var itemsToSkip = (CurrentPage.Value - 1) * ItemsPerPage;

        Employees = await context.Employees.Include(emp => emp.Department)
                                           .OrderBy(emp => emp.FirstName)
                                           .Skip(itemsToSkip) // skip items based on the CurrentPage parameter
                                           .Take(ItemsPerPage) // always take n items
                                           .ToArrayAsync();
    }
}
```
