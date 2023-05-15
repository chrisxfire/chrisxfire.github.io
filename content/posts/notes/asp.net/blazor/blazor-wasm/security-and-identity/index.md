---
title: "notes > asp.net > blazor > blazor wasm > security and identity > overview"
date: 2023-01-01T00:00:00-06:00
draft: true
---

# Overview
Since Blazor WASM is a client-side app, A&A must be performed on the server.

## Authentication Building Blocks
- `Microsoft.AspNetCore.Components.WebAssembly.Authentication` brings in support for OIDC (OpenID Connect)
- OIDC is the default authentication provider
- `AuthenticationStateProvider` service to understand the authentication state
- `CascadingAuthenticationState` cascades authentication state through the Component hierarchy
- `Duende IdentityServer` is the default identity provider
  - `Microsoft.AspNetCore.Components.WebAssembly.Authentication` supports other OIDC-compliant identity providers such as Okta, Auth0 (Aut0 was acquired by Okta), and Azure AD

## Authorization Building Blocks
- `AuthorizeView` Component to show or hide content in the UI based on whether the user is authorized.
- `[Authorize]` Attribute and Roles from ASP.NET Core

## Blazor's Default Security Behaviors
1. `[Authorize]` Attribute — when a Component is hit that has this attribute applied, the user is redirected to `/authentication/login` if the user has not yet authenticated.
2. After Successful Login — the user is redirected to `/authentication/login-callback`

# Auth0 External Identity Provider
- Auth0 can handle user login and user registration
- Auth0 is free for up to 7,000 users (even for commercial apps)

PKCE — Proof Key for Code Exchange

## Configuring Auth0
1. Create an Auth0 Account
2. Create an Application with Auth0
    1. manage.auth0.com > **Create Application** > application type = **Single Page Web Applications** > **Create**
    2. *Applications* > *Applications* 
        1. Copy the *Domain* and *Client ID*
        2. *Application URIs* 
            1. *Allowed Callback URLs* > **https://localhost:*portNumber*/authentication/login-callback**
            2. *Allowed Logout URLs* > **https://localhost:*portNumber*/**
    3. **Save Changes**

## Adding Auth0 Authentication Support to the App
### 1. Create or update `/wwwroot/appsettings.json`
```json
{
    "Auth0": {
        // The Authority scheme MUST be https, even if that is not what was copied from Auth0:
        "Authority": "<Domain copied fro Auth0>",
        "ClientId": "<Client ID copied from Auth0>"
    }
}
```

### 2. Add Authentication package and script references
`dotnet add package Microsoft.AspNetCore.Components.WebAssembly.Authentication`

`index.html`:
```html
<script src="_content/Microsoft.AspNetCore.Components.WebAssembly.AuthenticationService.js"></script>
```

### 3. Make middleware changes
`Program.cs`
```cs
// ...
builder.Services.AddOidcAuthentication(options => 
{ 
    builder.Configuration.Bind("Auth0", options.ProviderOptions);
    // specifies the "flow" to use (in this case, the authorization code flow):
    options.ProviderOptiosn.ResponseType = "code";
});

await builder.Build().RunAsync();
```

### 4. Update imports
`_Imports.razor`
```html
<!-- ... -->
@using Microsoft.AspNetCore.Authorization
@using Microsoft.AspNetCore.Components.Authorization
<!-- ... -->
```

### 5. Update the Router
`App.razor`
```html
<CascadingAuthenticationState>
    <Router AppAssembly="@typeof(App).Assembly" AdditionalAssemblies="@lazyLoadedAssemblies" OnNavigateAsync="@OnNavigateAsync">
        <Found Context="routeData">
            <!-- check to see if user is authenticated to see the requested page... -->
            <AuthorizeRouteView RouteData="@routeData" DefaultLayout="@typeof(MainLayout)">
                <!-- ...and show this message while checking: -->
                <Authorizing>
                    <p>Determining session state, please wait...</p>
                </Authorizing>
                <!-- if not authorized, display this message: -->
                <NotAuthorized>
                    <h1>Sorry</h1>
                    <p>You're not authorized to reach this page. You need to <a href="/authentication/login">log in.</a></p>
                </NotAuthorized>
            </AuthorizeRouteView>
            <FocusOnNavigate RouteData="@routeData" Selector="h1" />
        </Found>
        <NotFound>
            <PageTitle>Not found</PageTitle>
            <LayoutView Layout="@typeof(MainLayout)">
                <p role="alert">Sorry, there's nothing at this address.</p>
            </LayoutView>
        </NotFound>
    </Router>
</CascadingAuthenticationState>
```

### 6. Add code to allow users to log in
`Pages/Authentication.razor`
```html
@page "/authentication/{action}"
@using Microsoft.AspNetCore.Components.WebAssembly.Authentication
@using Microsoft.Extensions.Configuration

@inject NavigationManager Navigation
@inject IConfiguration Configuration

<!-- this Component handles user's auth status and interactions with Auth0's authentication server: -->
<RemoteAuthenticatorView Action="@Action">
    <LogOut>  
        @{
            var authority = (string)Configuration["Auth0:Authority"];
            var clientId = (string)Configuration["Auth0:ClientId"];
            
            <!-- disconnects from Auth0 on logout: -->
            Navigation.NavigateTo($"{authority}/v2/logout?client_id={clientId}");
        }
    </LogOut>
</RemoteAuthenticatorView>
```
```cs
@code {
    [Parameter] public string Action { get; set; }
}
```

`Components/AuthenticationStatus.razor`
```html
@using Microsoft.AspNetCore.Components.Authorization
@using Microsoft.AspNetCore.Components.WebAssembly.Authentication

@inject NavigationManager Navigation
@inject SignOutSessionStateManager SignOutManager

<AuthorizeView>
    <!-- if user is logged in: -->
    <Authorized>
        <h4>
            Hello, @context.User.Identity.Name!
            <!-- logout button: -->
            <a class="text-white text-decoration-none d-inline-block" href="#" @onclick="BeginSignOut">Log out</a>
        </h4>
    </Authorized>
    <!-- if user is not logged in: -->
    <NotAuthorized>
        <h4>
            <a class="text-white text-decoration-none" href="authentication/login">Log in</a>
        </h4>
    </NotAuthorized>
</AuthorizeView>
```
```cs
@code {
    private async Task BeginSignOut(MouseEventArgs args)
    {
        await SignOutManager.SetSignOutState();
        Navigation.NavigateTo("authentication/logout");
    }
}
```

`MainLayout.razor`
```html
<!-- ... -->
<li class="nav-item">
    <div class="nav-link">
        <AuthenticationStatus />
    </div>
</li>
<!-- ... -->
```

### 7. Secure Components with Authorization
1. Add the `Authorize` attribute to all Components that should not allow access without login:  

    `EmployeeOverview.razor`
    ```html
    @page "/employeeoverview"
    <PageTitle>@Title</PageTitle>
    <h2>Employee Overview</h2>
    @attribute [Authorize]
    <!-- ... -->
    ```

2. Use the `AuthorizeView` Component to only show content to logged in users:

    `NavMenu.razor`
    ```html
    <AuthorizeView>
        <NavLink ...>
            <span ...></span>
        </NavLink>
        <NavLink ...>
            <span ...></span>
        </NavLink>
    </AuthorizeView>
    ```
### 8. Secure API calls
1. Configure Auth0 for support for securing API calls:  
    manage.auth0.com > *Applications* > *APIs* > **Create API** > *Identifer* > **https://sampleapp.com/api** > **Create**

2. In the API project:
    1. Update `appsettings.json:`  
        ```json
        {
            // ...
            "Auth0": {
                // hostname only, no scheme prefix:
                "Domain": "<Domain copied fro Auth0>",
                "Audience": "https://sampleapp.com/api"
            },
            // ...
        }
        ```

    2. Add the JWT Bearer package:  
        `dotnet add package Microsoft.AspNetCore.Authentication.JwtBearer`

    3. Update Program.cs to use authorization based on bearer tokens:  
        ```cs
        // ...
        builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
                        .AddJwtBearer(JwtBearerDefaults.AuthenticationScheme, c =>
                        {
                            c.Authority = $"https://{builder.Configuration["Auth0:Domain"]}";
                            c.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters
                            {
                                ValidAudience = builder.Configuration["Auth0:Audience"],
                                ValidIssuer = $"https://{builder.Configuration["Auth0:Domain"]}"
                            };
                        });
        // ...
        // add A&A middleware:
        app.UseAuthentication();
        app.UseAuthorization();
        // ...
        ```

    4. Add the Authorize attribute to the Controllers:
        `EmployeeController.cs`
        ```cs
        [Route("api/[controller]")]
        [ApiController]
        [Authorize]
        public class EmployeeController : Controller
        {
            // ...
        }
        ```

3. In the App project:
    1. Update the `HttpClient`s in the DI container to use the JWT token for any API calls sent:   
        `Program.cs`
        ```cs
        // ...
        // update the HttpClient's in the DI container to use the BaseAuthorizationMessageHandler
        builder.Services.AddhttpClient<IEmployeeDataService, EmployeeDataService>(client => 
            client.BaseAddress = new Uri(builder.hostEnvironment.BaseAddress))
                                        .AddHttpMessageHandler<BaseAddressMessageHandler>();
        // ...
        ```
    
    2. Update the `AddOidcAuthentication` `ProviderOptions`:  
        `Program.cs`
        ```cs
        // ...
        builder.Services.AddOidcAuthentication(options => 
        { 
            builder.Configuration.Bind("Auth0", options.ProviderOptions);
            // specifies the "flow" to use (in this case, the authorization code flow):
            options.ProviderOptions.ResponseType = "code";
            options.ProviderOptions.AdditionalProviderParameters.Add("audience", builder.Configuration["Auth0:Audience"]);
        });
        // ...
        ```
    
    3. Add the Audience to appsettings.json:
        `appsettings.json`
        ```json
        {
            "Auth0": {
                // ...
                "Audience": "https://exampleapp.com/api"
            }
        }
        ```