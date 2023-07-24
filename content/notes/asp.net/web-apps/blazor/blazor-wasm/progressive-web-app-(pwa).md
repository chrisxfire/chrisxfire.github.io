---
title: notes > asp.net > web apps > blazor > blazor wasm > progressive web app (pwa)
date: 2023-07-23T00:00:00-06:00
draft: false
weight: 1
---

# Overview
A Blazor WASM PWA is a SPA that uses modern browser APIs and capabilities to behave like a desktop app. *Progressive* means that:
- A user may discover the app within their browser (like any other SPA)
- Later, the user *progresses* to installing it on their OS.

Blazor PWAs can be created from project templates or existing Blazor WASM apps can be converted to PWAs.
- Documentation: https://learn.microsoft.com/en-us/aspnet/core/blazor/progressive-web-app?view=aspnetcore-7.0

# Creating from CLI
```powershell
dotnet new blazorwasm -o APPNAME --pwa
```

# Converting Existing Blazor WASM app to PWA
1. Update the project file:  
   `SomeProject.csproj`
   1. Add the `ServiceWOrkerAssetsManifest` to a `PropertyGroup`:

        ```xml
        ...
            <ServiceWorkerAssetsManifest>service-worker-assets.js</ServiceWorkerAssetsManifest>
        </PropertyGroup>
        ```
    2. Add this `ServiceWorker` to an `ItemGroup`:
        ```xml
        <ItemGroup>
         <ServiceWorker Include="wwwroot\service-worker.js" 
                        PublishedContent="wwwroot\service-worker.published.js" />
        </ItemGroup>
        ```
2. Obtain the static assets:  
   1. Create a new, separate PWA project:
        ```powershell
        dotnet new blazorwasm -o TempProject --pwa
        ```
   2. From that project, find these files and copy them to your current project's `wwwroot` folder: `icon-512.png`, `manifest.json`, `service-worker.js`, `service-worker.published.js`
   3. In your current project's `wwwroot/index.html` file:
      1. Add these two \<link\> elements:
         ```html
         <link href="manifest.json" rel="manifest" />
         <link rel="apple-touch-icon" sizes="512x512" href="icon-512.png" />
         ```
      2. Add this \<script\> tag inside the closing </body\> tag immediately after the `blazor.webassembly.js` script tag:
         ```html
                ...
                <script>navigator.serviceWorker.register('service-worker.js');
            </script>
         </body>

         ``

# Offline Support
By default, apps created with the PWA template have support for running offline.  This is enabled by the service workers included in the template:
- `wwwroot/service-worker.js` — used during development
- `wwwroot/service-worker.published.js` — used after app is published'

## Considerations
Offline support is only relevant if:
- The primary data store is local to the browser (like when using localStorage or IndexedDB).
- There is a requirement for the user to view the data offline.
- The goal is to guarantee that the app loads immediately regardless of network conditions.

Offline support is only enabled when published (not in development).

## Cache-first Fetch Strategy
`service-worker.published.js` resolves request using a *cache-first* strategy: the service worker will prefer to return cached content, regardless of whether the user has network access, and *even if newer content* is available on the server. 

To prevent this, update this script in `wwwroot/index.html`:
```html
<script>
    navigator.serviceWorker.register('/service-worker.js', {updateViaCache: 'none'});
</script>
```

The service worker tries to serve cached content whenever available.  If none is available for a certain URL, then it falls back on a network request.  This logic is in the `onFetch` function in `service-worker.published.js`.

### Server-rendered Pages
The service worker resolves requests by returning cached content for `/index.html` — regardless of the requested URL.  Specifically, it intercepts requests and resolves them using `/index.html`.  If your app has certain URLs that must return server-rendered HTML, edit the logic in the service worker:  
`service-worker.published.js`
```js
const shouldServeIndexHtml = event.request.mode === 'navigate'
 // Add this line:
 && !event.request.url.includes('/CERTAIN-URL/');

```

### Controlling Asset Caching
Modify asset caching by editing the logic in `onInstall` in `service-worker.published.js`.  By default, the cache includes `.html`, `.css`, `.js`, and `.wasm` files.

It also includes all static assets in `wwwroot`.  If there are millions of these assets, the service worker will fetch and cache them all.  Implement logic in `onInstall` to control which subset should be fetched and cached.

To add additional resources that are not present in wwwroot (and, by extension, not in the asset cache), add `ItemGroup` entries in the project file:  
`SomeProject.csproj`
```xml
<ItemGroup>
    <ServiceWorkerAssetsManifestItem Include="MyDirectory\AnotherFile.json"
                                     RelativePath="MyDirectory\AnotherFile.json"
                                     AssetUrl="files/AnotherFile.json" />
</ItemGroup>

```

Note that this will *not* cause the item to be published in wwwroot; publishing output most be controlled separately.

## Background Updates
Blazor PWA apps automatically try to update themselves in the background.  Here's how this works:
- When compiled, the project generates a service worker assets manifest (`service-worker-assets.js`) that lists all the static resources the app requires and hashes of those resources.
- Each time the user visits the app, the browser re-requests `service-worker.js` and the assets manifest.
  - The files are compared byte-for-byte.
  - If either has changed, the service worker attempts to install a new version of itself.
    - To do this, it creates a new, separate cache and populates it with the sources listed in the assets manifest. (This logic is in the `onInstall` function in `service-worker.published.js`.)
    - If successful, the new service worker enters a *waiting for activation* state.
      - When the user closes all instances of the app, the new service worker enters the *active* state and the old service worker and its cache are deleted.
      - Note: During development, [this phase can be skipped](https://web.dev/service-worker-lifecycle/#skip-waiting).
    - If not successful, the new service worker is discarded, and the process is attempted again the next time the user visits the app.


### Considerations
- If you deploy backward-incompatible API schema changes before all users have upgraded the app, the client app will break for users who have not yet updated. 
  - Block users from using incompatible older versions of the app.   Use [ServiceWorkerRegistration](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorkerRegistration) to determine whether the app is up to date and, if not, prevent usage until it is.

# Push Notifications
The mechanism for sending push notifications is implemented in the backend server.  For an example, [see here](https://github.com/dotnet-presentations/blazor-workshop/blob/main/docs/09-progressive-web-app.md#sending-push-notifications).  

The mechanism for receiving a push notification is implemented in the service worker file.  For an example, [see here](https://github.com/dotnet-presentations/blazor-workshop/blob/main/docs/09-progressive-web-app.md#displaying-notifications).

# [Authentication](https://learn.microsoft.com/en-us/aspnet/core/blazor/progressive-web-app?view=aspnetcore-7.0&tabs=visual-studio#interaction-with-authentication)
The PWA template supports authentication.  To implement authentication in an offline PWA:
1. Replace the `AccountClaimsPrincipleFactory<TAccount>` with a factory that stores the last signed-in user and users the stored user when the app is offline.
2. Queue operations while the app is offline and apply them when it reconnects.
3. During sign out, clear the stored user.

See [this sample app](https://github.com/SteveSandersonMS/CarChecker) for details.
