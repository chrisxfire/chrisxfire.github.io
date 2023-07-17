---
title: notes > web development > msid > msal
date: 2022-05-10T17:32:57-0600
draft: false
weight: 1
---
# MSAL – Microsoft Authentication Library
Provides secure access to Graph, other Microsoft APIs, 3rd-party web APIs, or your own web API.

# Authentication flows
- Authorization code – apps securely obtain tokens in the name of the user.
- Client credentials – service applications run without user interaction.
- On-behalf-of – App calls a service/web API which in turn calls Graph.
- Implicit – used in browser-based apps.
- Device code – sign in to a device from another device with a browser.
- Integrated windows – Windows PCs silently acquire an access token when domain-joined.
- Interactive – apps call Graph in the name of the user.
- Username/password

# Application categories
- Public client apps – apps run on devices or in a web browser; not trusted to safely keep app secrets; cannot hold client secrets.
- Confidential client apps – apps that run on servers; considered difficult to access; capable of keeping an app secret.

# Initializing client applications
Register the app in the Azure portal and note:
1.  client ID (GUID)
2.  identity provider URL (instance) and sign-in audience for the app
3.  tenant ID
4.  app secret (client secret string) or certificate (X509Certificate2)

# Write code
## Client app builders
```cs
// For public client applications:
IPublicClientApplication app = PublicClientApplicationBuilder.Create(clientId).Build();

// For confidential client applications:
string redirectUri = "https://myapp.azurewebsites.net";
IConfidentialClientApplication app = ConfidentialClientApplicationBuilder.Create(clientId)
    .WithClientSecret(clientSecret)
    .WithRedirectUri(redirectUri )
    .Build();
```

## Builder modifiers
- `.WithAuthority` - Sets app default authority to an AAD authority; can be Azure Cloud, audience, tenant (via - tenant ID or domain name), or the authority URI directly.
- `.WithTenantId` - Overrides the tenant ID or the tenant description.
- `.WithClientId` - Overrides the client ID.
- `.WithRedirectUri` - Overrides the default redirect URI; useful when a broker is involved.
- `.WithComponent` - Sets name of the library using MSAL.NET (telemetry).

## For confidential client app builder only
- `.WithCertificate` - Sets the certificate identifying the app with AAD.
- `.WithClientSecret` - Sets the client secret (app password) identify the app with AAD.

## Acquire a token
```cs
// Set the scopes:
string[] scopes = { "user.read" };

// Request the token
AuthenticationResult result = await app.AcquireTokenInteractive(scopes).ExecuteAsync();

// The token is stored in result.AccessToken.
```
