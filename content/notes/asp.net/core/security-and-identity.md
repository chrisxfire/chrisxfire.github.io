---
title: "notes > asp.net > core > security and identity"
date: 2023-05-14T00:00:00-06:00
draft: false
---

<style>
    r { color: red }
    o { color: orange }
    g { color: green }
</style>

# ASP.NET Core Identity
- A&A system that supports UI login functionality
- Not for APIs
- Supports external service providers
- Supports MVC & Razor Pages, scaffolding, SQL Server
- Includes a Razor Class Library for identity-enabled Views that typically need to be included in a web app

# Important Classes
## `UserManager<IdentityUser>`
Manages all interaction (CRUD operations) with user objects in the datastore.

## `SignInManager<IdentityUser>`
User authentication and related actions; defines methods such as `PasswordSignInAsync`, `ConfirmEmailAsync`, `SignOutAsync`, etc.

# Adding ASP.NET Core Identity to an App
## Configuring
1. Add required packages  
    `dotnet add package microsoft.aspnetcore.identity.entityframeworkcore`  
    `dotnet add package microsoft.aspnetcore.identity.ui`  

2. Update the `DbContext`
    ```cs
    using Microsoft.AspNetCore.Identity.EntityFrameworkCore;
    public class BethanysPieShopDbContext : IdentityDbContext // must inherit from this base class
    ```
    3. Add identity services to DI container
    `Program.cs`
    ```cs
    builder.Services.AddDefaultIdentity<IdentityUser>(options => // IdentityUser is a built-in type to represent a user
    { 
        // registration will only succeed if these conditions are met:
        options.Password.RequireDigit = true;
        options.Password.RequiredLength = 8;
        options.Password.RequireNonAlphanumeric = true;
        options.User.RequireUniqueEmail = true;
    })
    .AddEntityFrameworkStores<BethanysPieShopDbContext>(); // use EF for identity data
    ```
4. Add authentication middlewareZ
    ```cs
    app.UseAuthentication();
    ```
5. Run a build

6. Create a migration
Creates an ASP.NET `Roles`, `Users`, `RoleClaims`, `UserClaims`, `UserLogins`, and other tables:
    pmc > `add-migration IdentityAdded`  
    pmc > `update-database`
	
## Adding Authentication
Two techniques:  manual approach or scaffolding

### Scaffolding
1. Right-click project > **Add** > **New Scaffolded Item…** > **Identity** > **Add** > check **Override all files** OR check specific items > Data context class: *SomeDbContext* > **Add**
This will, among other things, make changes to `Program.cs`.  
Adds:   
`Areas` > `Identity` > `Pages` >  
                    `_ValidationScriptsPartial.cshtml`, `_ViewImports.cshtml`, `_ViewStart.cshtml`  
                    `Account` >  
                        `_ViewImports.cshtml`  
                        `Login.cshtml` — the Login UI  
                        `Register.cshtml` — the UI to register a new account  

2. Update layout to account for scripts that scaffolding added:  
`/Views/Shared/_Layout.cshtml`  
    Below `@RenderBody()`  
    `@RenderSection("Scripts", required: false)`
        
3. Update layout to add the login partial:  
`/Views/Shared/_Layout.cshtml`
    ```html
        <partial name="_LoginPartial" />
    ```
## Adding Authorization
1. Add authorization middleware:  
    `Program.cs`  
    ```cs
    app.UseAuthorization();
    ```
2. Decorate Controller and/or Action(s) with `Authorize` attribute  
    `[Authorize]` attribute  
        - Can be added to Controller to a Controller's Action
        - Confirms user is logged in before proceeding
        
    `[Authorize(Roles = "RoleGroup")]`
        - Checks if user is logged in AND if user is part of RoleGroup before proceeding

    Example
    ```cs
    [Authorize]
    public class OrderController : Controller
    {
        [Authorize] // requires user to be logged in to use this method
        public IActionResult Checkout()
        {
        }
    }
    ```
