---
title: depenency injection
date: 2023-04-17T00:00:00-06:00
draft: false
weight: 1
---

# default services
- `HttpClient` (Scoped)
- `IJSRuntime` (Server=Scoped, WASM=Singleton) — an instance of a JavaScript runtime where JS calls are dispatched
- `NavigationManager` (Server=Scoped, WASM=Singleton) — helpers for working with URIs and navigation state

# requesting services in components
Inject services into components using `@inject` directive:  
```html
@page "/customer-list"
@* Inject type into property *@
@inject IDataAccess DataRepository

@if (customers != null)
{
    <ul>
        @foreach (var customer in customers)
        {
            <li>@customer.FirstName @customer.LastName</li>
        }
    </ul>
}
```
```cs
@code {
    private IReadOnlyList<Customer>? customers;

    protected override async Task OnInitializedAsync()
    {
        customers = await DataRepository.GetAllCustomersAsync();
    }

    private class Customer
    {
        public string? FirstName { get; set; }
        public string? LastName { get; set; }
    }

    private interface IDataAccess
    {
        public Task<IReadOnlyList<Customer>> GetAllCustomersAsync();
    }
}
```
If a base class is required for a component, and injected properties are required for that component, use the `[Inject]` attribute:
```cs
using Microsoft.AspNetCore.Components;

public class ComponentBase : IComponent
{
    [Inject]
    // Do not mark injected services nullable.  Use a default value instead.
    protected IDataAccess DataRepository { get; set; }
    ...
}
```
In components derived from the base class, the `@inject` directive is not necessary.

# managing di scope
## `OwningComponentBase`
Use `OwningComponentBase` to limit a service's lifetime in Blazor apps.  `OwningComponentBase` has property `protected IServiceProvider ScopedServices` and creates a DI scope corresponding to the lifetime of the component.  This allows DI services with a scoped lifetime to live as long as the component.

If a service is injected into a component with `@inject` or `[Inject]` are not created in the component's scope.  They must be resolved from `ScopedServices.`

`Pages/TimeTravel.razor`
```html
@page "/time-travel"
@inject ITimeTravel TimeTravel1
@inherits OwningComponentBase

<h1><code>OwningComponentBase</code> Example</h1>

<ul>
    <li>TimeTravel1.DT: @TimeTravel1?.DT</li> @* receives service from DI container *@
    <li>TimeTravel2.DT: @TimeTravel2?.DT</li> @* receives service from OwningComponentBase.ScopedServices *@
</ul>
```
```cs
@code {
    private ITimeTravel? TimeTravel2 { get; set; }

    protected override void OnInitialized()
    {
        TimeTravel2 = ScopedServices.GetRequiredService<ITimeTravel>();
    }
}
```
`Shared/NavMenu.razor`
```html
<div class="nav-item px-3">
    <NavLink class="nav-link" href="time-travel">
        <span class="oi oi-list-rich" aria-hidden="true"></span> Time travel
    </NavLink>
</div>
```
Initially navigate to TimeTravel component.  Output:
```
TimeTravel1.DT: 8/31/2022 2:54:45 PM
TimeTravel2.DT: 8/31/2022 2:54:45 PM
```
Navigate away and back again.  Output:
```
// value the same since TimeTravel1 has same service instance from when component was first created; tied to the user's circuit:
TimeTravel1.DT: 8/31/2022 2:54:45 PM 
// value is different since TimeTravel2 obtains a new TimeTravel instance:
TimeTravel2.DT: 8/31/2022 2:54:59 PM
```

## `OwningComponentBase<T>`
`OwningComponentBase<T>` has a Service property that returns an instance of `T` from the scoped DI container.  Use this when there's only one primary service the app needs from the DI container using the component's scope.  The `ScopedServices` property is still available if needed:
```html
@page "/users"
@attribute [Authorize]
@inherits OwningComponentBase<AppDbContext>

<h1>Users (@Service.Users.Count())</h1>

<ul>
    @foreach (var user in Service.Users)
    {
        <li>@user.UserName</li>
    }
</ul>
```


