---
title: notes > code > web > msid > microsoft identity platform
date: 2022-05-10T16:54:55-0600
draft: false
weight: 1
---
# Components
- OAuth 2.0 and OpenID Connect
  - Microsoft work/school accounts via Azure AD
  - Personal Microsoft accounts
  - Social or local accounts via Azure AD B2C
- MSAL
- App management portal
- App configuration API and PowerShell

# Service Principals
- Applications must be reigstered with an Azure AD tenant.
- Apps can be registered in Azure portal as:
  - Single-tenant (only your tenant)
  - Multi-tenant (other tenants)
- Apps registered in Azure portal receive:
  - App object (globally unique instance of the app)
    - One and only one per app.
    - Resides in the Azure AD tenant where the app was registered (the app's "home" tenant).
    - Serves as a template for one or more service principal objects: properties apply to all service principal objects.
    - Defines:
      - How the service can issue tokens to access the app.
      - Resources the app might need to access.
      - Actions the app can take.
  - Service principal object
    - Created in every tenant where the app is used.
    - Security principals exist for users (user principals) and apps (service principals).
      - Defines the access policy and permissions for the user/app.
        - This enables authentication and authorization.
    - Application service principals: the application instance of a global app object in a single tenant.
    - Managed identity service principals: managed identities provide an identity for applications to use when connecting to resources that support AAD authentication.
    - Legacy service principals: A legacy app (an app created before app registrations were introduced). These have no associated app registrations.
  - The app object is the *global* representation of the app for use across all tenants. The service principal is *local* representation in a specific tenant.

# Permissions and Consent
- OAuth 2.0: a method through which a 3rd party app can access web-hosted resources (like Microsoft Graph, M365 Mail API, Azure Key Vault, etc.) on behalf of a user.
- Scopes: permission sets (or just "permissions"). Represented in a string value.
  - Example: <https://graph.microsoft.com/Calendars.Read> requests permission to read users calendars.
    - If the host portion if left off, it is assumed to be graph.microsoft.com.
- The `scope` query parameter holds the permissions the app needs.

## Permission Types
- Delegated – for apps that have a signed-in user present.
- Application – for apps that run without a signed-in user present (services, daemons).

## Consent Types
- Static user consent
  - You must specify all the permissions it needs, and will ever need, in the app's configuration in the Azure portal.
  - Also enable administrators to consent on behalf of all users in the organization.
- Incremental user consent
  - Ask for a minimum set of permissions up front and request more as needed.
  - New scopes are included in the `scope` parameter.
  - If app requires admin privileged permissions, you must register all of the permissions in the Azure portal (not just the subset that require admin consent).
- Admin consent
  - Required for high-privilege permissions.
  - Admin consent provided on behalf of an organization still requires the static permissions registered for the app.

# Conditional Access
Conditional Access allows for MFA, allowing only Intune-enrolled devices to access specific services, and geolocation and IP range restrictions.
- Scenarios that require code to handle Conditional Access challenges
  - Apps performing the on-behalf-of flow.
  - Apps accessing multiple services/resources.
  - SPAs using MSAL.js.
  - Web apps calling a resource.
