---
title: app service
date: 2023-01-13T20:57:52-0700
draft: false
weight: 1
---
# Overview
An HTTP-based services for hosting web apps, REST APIs, and mobile back-ends.

Features:
- Automatic scaling (horizontally and vertically)
- CI/CD (Azure DevOps, GitHub, Bitbucket, FTP, local Git repo)

# App Service Plans
A set of compute resources for a web app to run.
- One or more apps can be configured on an app service plan
- Azure Functions can also run in an app service plan

# Deployments
Deploy to Azure App Service:
- Automated deployments—Azure DevOps, GitHub, Bitbucket
- Manual deployments—Git, CLI (az), Zip (curl), FTP/S

# Auth & Auth
Optional, built-in authentication
Identity providers:
- Microsoft Identity Platform at `/.auth/login/aad`
- Facebook at `/.auth/login/facebook`
- Google at `/.auth/login/google`
- Twitter at `/.auth/login/twitter`
- Any OpenID Connect provider at `/.auth/login/*provider-name*`

## How it Works
The authentication and authorization module runs in the same sandbox as an app. All incoming HTTP requests pass through this module. The module :
- Authenticates users
- Manages tokens
- Manages the authenticated session
- Injects identity information into request headers

The module is configured with app settings.

## Authentication Flows
| Step                | Without provider SDK                                                          | With provider SDK                                     |
|---------------------|-------------------------------------------------------------------------------|-------------------------------------------------------|
| Sign user in        | Redirect client to `/.auth/login/*provider*`          | Client code signs user in and receives auth token     |
| Post authentication | Redirect client to `/.auth/login/*provider*/callback` | Client code posts token                               |
| Establish session   | App Service adds authenticated cookie to response                             | App Service returns its own auth token to client code |
| Save content        | Client includes auth cookie in subsequent requests                            | Client code presents auth token in specific header    |

## Authorization Behavior
App Service can be configured to:
- Allow unauthenticated requests—defers authorization of unauthenticated traffic to application code. For authenticated requests, passes along auth information in HTTP headers.
- Require authentication—reject any authenticated traffic to application. Rejection can be a redirect action, an HTTP/401 Unauthorized response, or HTTP/403 Forbidden response.

# Networking
## Multi-tenant
Applies to Free, Shared, Basic, Standard, Premium/V2/V3 app service plans.
In multi-tenant, many different customers exist on the same network.
*Front ends*—roles that handle incoming requests.
*Workers*—roles that host customer workloads.

| For this use case…                                        | …use this feature    |
|-----------------------------------------------------------|----------------------|
| IP-based SSL                                              | App-assigned address |
| Unshared dedicated inbound address                        | App-assigned address |
| Restrict access to app from set of well-defined addresses | Access restrictions  |

Outbound addresses
- Shared by other tenants
- Changing app service plans results in change of outbound IP addresses
- Outbound addresses used by an app are listed in the app's properties

Find Currently-Used Outbound IPs via Cloud Shell
```powershell
az webapp show \
--resource-group <group_name> \
--name <app_name> \
--query outboundIpAddresses \
--output tsv
```
Find All Possible Outbound IPs via Cloud Shell
```powershell
az webapp show \
--resource-group <group_name> \
--name <app_name> \
--query possibleOutboundIpAddresses \
--output tsv
```
