---
title: notes > code > web > msid > msgraph
date: 2022-05-11T13:35:11-0600
draft: false
---
# Microsoft Graph
Unified API model to access data in M365.

## 3 components
- Graph API (https://graph.microsoft.com/)
- Graph connectors (deliver data outside of Microsoft cloud into Graph)
- Graph Data Connect (deliver Graph data to Azure data stores)

Primary namespace: `microsoft.graph`

# Call a REST API Method
Syntax:  {HTTP method} https://graph.microsoft.com/{version}/{resource}?{query-parameters}   
Example: `GET https://graph.microsoft.com/%7bversion%7d/%7bresource%7d?%7bquery-parameters%7d`

# HTTP Methods
- `GET, POST, PATCH, PUT, DELETE.`
- `GET` and `DELETE` do not require a request body.
- `POST, PATCH, PUT` usually require a request body in JSON.

# Microsoft Graph .NET SDK
## Packages
- `Microsoft.Graph` – service library that contains models and request builders.
- `Microsoft.Graph.Core` – core library for making calls to Microsoft Graph.

# Code
## Create a Graph Client
Use a single client for the lifetime of the application.
```cs
// Build a client application.
IPublicClientApplication publicClientApplication = PublicClientApplicationBuilder
    .Create("INSERT-CLIENT-APP-ID")
    .Build();

// Create an authentication provider by passing in a client application and graph scopes.
DeviceCodeProvider authProvider = new DeviceCodeProvider(publicClientApplication, graphScopes);

// Create a new instance of GraphServiceClient with the authentication provider.
GraphServiceClient graphClient = new GraphServiceClient(authProvider);
```

## Read Information
```cs
// GET https://graph.microsoft.com/v1.0/me

var user = await graphClient.Me
    .Request()
    .GetAsync();
```

## Retrieve a List of Entities
```cs
// GET https://graph.microsoft.com/v1.0/me/messages?$select=subject,sender&$filter=<somecondition>&orderBy=receivedDateTime

var messages = await graphClient.Me.Messages
    .Request()
    .Select(m => new {
        m.Subject,
        m.Sender
    })
    .Filter("<filter condition>")
    .OrderBy("receivedDateTime")
    .GetAsync();
```

## Delete an Entity
```cs
// DELETE https://graph.microsoft.com/v1.0/me/messages/{message-id} (https://graph.microsoft.com/v1.0/me/messages/%7bmessage-id%7d)

string messageId = "AQMkAGUy...";
var message = await graphClient.Me.Messages[messageId]
    .Request()
    .DeleteAsync();
```

## Create a New Entity
```cs
// POST https://graph.microsoft.com/v1.0/me/calendars

var calendar = new Calendar
{
    Name = "Volunteer"
};

var newCalendar = await graphClient.Me.Calendars
    .Request()
    .AddAsync(calendar);
```

# Documentation
- [Microsoft Graph documentation | Microsoft Docs](https://docs.microsoft.com/en-us/graph/)
- [Overview of Microsoft Graph - Microsoft Graph | Microsoft Docs](https://docs.microsoft.com/en-us/graph/overview)
- [Microsoft Graph tutorials | Microsoft Docs](https://docs.microsoft.com/en-us/graph/tutorials)
- [Microsoft Graph auth overview | Microsoft Docs](https://docs.microsoft.com/en-us/graph/auth/)
- [Use the Microsoft Graph API - Microsoft Graph | Microsoft Docs](https://docs.microsoft.com/en-us/graph/use-the-api)
- [Graph Explorer - Microsoft Graph](https://developer.microsoft.com/en-us/graph/graph-explorer)
- [Microsoft GraphSDKsoverview - Microsoft Graph | Microsoft Docs](https://docs.microsoft.com/en-us/graph/sdks/sdks-overview)
- SDK: [microsoftgraph/msgraph-sdk-dotnet: Microsoft Graph Client Library for .NET! (github.com)](https://github.com/microsoftgraph/msgraph-sdk-dotnet)
