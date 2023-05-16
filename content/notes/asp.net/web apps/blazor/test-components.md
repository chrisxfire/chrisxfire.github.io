---
title: "notes > asp.net > web apps > blazor > test components"
date: 2023-05-16T00:00:00-06:00
draft: false
---

<style>
    r { color: red }
    o { color: orange }
    g { color: green }
</style>

# Testing with bUnit - Overview
bUnit extends other unit testing frameworks (xUnit, Nunit, MSTest, etc) for Blazor-specific unit tests.

## Features
- includes a *semantic HTML comparer* so that not all possible cases must be manually tested.
- supports dependency injection and passing parameters
- testing user interactions and event handlers
- testing IJSRuntime
- testing authorization
- mocking an HttpClient

## Simple Unit Test Example
```cs
public void CanUpdatePiePrice() 
{
    // Arrange
    var pie = new Pie() { Name = "Sample pie", Price = 12.95M };

    // Act
    pie.Price = 20M;

    // Assert
    Assert.Equal(20M, pie.Price);
}
```

# Using bUnit
## Process
1. Install the bUnit Visual Studio template  
    `dotnet new --install bunit.template`
2. Create a bUnit project  
    `dotnet new bunit --framework xunit -o project-name`
3. Add the bUnit project to your Solution
4. From the bUnit project, add a project reference to the main project
5. Start writing unit tests  

## Writing Unit Tests
bUnit supports writing tests in C# (`.cs`) or Razor files (`.razor`).

### Razor Example
Assuming this Component:  
`MainProject/Components/SampleComponent.razor`
```html
<h3>Inbox</h3>

@if (@MessageCount > 0)
{
    <h4>You currently have @MessageCount questions from employees!</h4>
}
else
{
    <h4>No questions from employees! All good!</h4>
}
```
```cs
@code
{
    [Parameter]
    public int MessageCount { get; set; }
}
```

Unit test for the above Component:  
`TestProject/SampleComponentTests.razor`
```cs
@code {
    [Fact]
    public void RenderSampleComponentWithValueGreaterThanZero()
    {
        // Arrange
        // TestContext provides access to the Component
        using var ctx = new TestContext();

        // Act
        // cut = component under test
        // use the context's Render method and pass in the Component to be tested, including a test value for the MessageCount parameter:
        var cut = ctx.Render(@<SampleComponent MessageCount="3" />);

        // Assert
        // pass in the expected HTML output:
        cut.MarkupMatches("<h3>Inbox</h3><h4>You currently have 3 questions from employees!</h4>"); 
    }

    [Fact]
    public void RenderSampleComponentWithZero()
    {
        // Arrange
        using var ctx = new TestContext();

        // Act
        var cut = ctx.Render(@<SampleComponent MessageCount="0" />);

        // Assert
        cut.MarkupMatches("<h3>Inbox</h3><h4>No questions from employees! All good!</h4>"); 
    }
}
```

Alternatively, inherit `TestContext` to avoid creating one in each method:
```cs
@inherits TestContext

@code
{
    [Fact]
    public void RenderSampleComponentWithValueGreaterThanZero()
    {
        var cut = ctx.Render(@<SampleComponent MessageCount="3" />);

        cut.MarkupMatches("<h3>Inbox</h3><h4>You currently have 3 questions from employees!</h4>"); 
    }
    // ...
}
```

### Test only a part of a Component
`TestProject/EmployeeCardTests.razor`
```cs
@using BethanysPieShopHRM.Shared.Domain

@inherits TestContext

@code 
{
    private Employee _employee;

    public EmployeeCardTests()
    {
        var jobCategory = new JobCategory { JobCategoryId = 3, JobCategoryName = "Management" };
        var country = new Country { CountryId = 1, Name = "Belgium" };

        _employee = new Employee()
        {
            MaritalStatus = MaritalStatus.Single,
            BirthDate = new DateTime(1989, 3, 11),
            City = "Brussels",
            Email = "bethany@bethanyspieshop.com",
            EmployeeId = 1,
            FirstName = "Bethany",
            LastName = "Smith",
            Gender = Gender.Female,
            PhoneNumber = "324777888978978",
            Smoker = false,
            Street = "Grote Markt 1",
            Zip = "1000",
            JobCategory = jobCategory,
            JobCategoryId = jobCategory.JobCategoryId,
            Comment = "Lorem Ipsum",
            ExitDate = null,
            JoinedDate = new DateTime(2015, 3, 1),
            Country = country,
            CountryId = country.CountryId
        };
    }

    [Fact]
    public void RenderEmployeeCardDetailNavLink()
    {
        // render the Component:
        var cut = Render(@<EmployeeCard Employee="_employee" />);

        // find an element by ID and test that its markup matches
        // note that the attributes listed (href, id, class) do not have to be in the same order as in the code:
        cut.Find("#detailnavlink").MarkupMatches(
            @"<a href=""employeeedit/1"" id=""detailnavlink"" class=""btn btn-outline-primary btn-sm mb-1"">Edit employee</a>");
    }
}
```

## Writing Advanced Unit Tests
### Testing an injected service
`TestProject/InboxWidgetTests.razor`
```cs
@using BethanysPieShopHRM.App.Components.Widgets
@using BethanysPieShopHRM.App

@inherits TestContext

@code
{
    public InboxWidgetTests() 
    {
        // bUnit exposes the services collection on the TestContext, so services can be injected into the test:
        this.Services.AddScoped<ApplicationState>();
    }

    [Fact]
    public void RenderInboxWidgetWIthValueGreaterThanZero()
    {
        // access the ApplicationState service:
        var applicationState = this.Services.GetService<ApplicationState>();
        applicationState.NumberOfMessages = 5;

        var cut = Render(@<InboxWidget />);
        cut.MarkupMatches("<h3>Inbox</h3><h4>You currently have 5 questions from employees!</h4>");
    }
}
```