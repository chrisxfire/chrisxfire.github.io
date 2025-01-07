---
title: cross origin resource policy
date: 2025-01-06T00:00:00-06:00
draft: true
weight: 1
tags:
 - kb/web-dev/security/cross-origin-security-headers
---

# [`Cross-Origin-Resource-Policy` (CORP) to prevent hotlinking and XSSI attacks](https://andrewlock.net/understanding-security-headers-part-1-cross-origin-opener-policy-preventing-attacks-from-popups/)
The same-origin policy restricts many JavaScript APIs and requests that use `fetch()`, but restricts few *embedded* resources. The [list of resources
which can be accessed cross-origin](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy#cross-origin_network_access) is 
long and includes resources in `<img>`, `<video>`, and `<audio>` elements, `<script>` elements, and CSS files in `<link rel=...>` elements. 

## hotlinking
There's nothing in the same-origin policy that prevents others from linking to the above resources on your site and displaying it on theirs.
This is called *hotlinking*. 

## vulnerabilities
Cross Site Script Inclusion (XSSI) vulnerabilities involve a script from your site that is embedded inside an attacker's site. This can leak
senstive data.

## same-origin vs. same-site
Two of the Cross-Origin-Resource-Policy header values (as explained below) are `same-origin` and `same-site`:
- `same-origin` requires a matching scheme, domain, subdomain and port.
- `same-site` requires a matching scheme and domain.
- Neither considers the path, querystring, or fragment of the URL.

### `Cross-Origin-Resource Policy`
`Cross-Origin-Resource Policy` is a security header that can be returned in HTTP responses that signals to the browser whether or not the
resource is allowed to be embedded in the document. It has three possible values:
1. `same-origin` — most restrictive; the browser must reject cross-origin responses.
2. `same-site` — less restrictive; the browser must reject cross-site responses.
3. `cross-origin` — least restrictive; the browser must allow cross-origin responses.

The `same-site` value is useful when serving resources from a dedicated subdomain (like `cdn.example.com`) that you want embedded on `example.com`.

> [!NOTE]  
> CORP only applies to scenarios where `Cross-Origin-Resource-Sharing` (CORS) doesn't apply.  

#### scenarios
Consider two web apps:
1. Hosted at `localhost:5011` that serves an `Index.html` that hotlinks to an image at #2.
2. Hosted at `localhost:5005` that serves the image. 

> Scenario 1
- No `Cross-Origin-Resource-Policy` header value is set.
- Result: App 1 loads the image successfully.

> Scenario 2
- `Cross-Origin-Resource-Policy: cross-origin` is set.
- Result: App 1 loads the image successfully.

> Scenario 3
- `Cross-Origin-Resource-Policy: same-origin` is set.
- Result: App 1 fails to load the image.

### CORP vs. CORS
- CORS (`Cross-Origin-Resource-Sharing`) is used to allow cross-origin requests that would otherwise be blocked by the same-origin policy. 
- Adding a CORS header to a site *reduces* its security by *allowing* more requests.
	- These are called `cors` mode requests.
- Adding a CORP header to a site *increases* its security by *blocking* requests that would have otherwise been allowed despite the same-origin policy.
	- These are called `no-cors` mode requests.

Resources loaded by `<img>` tags, for example, are typically `no-cors` requests: CORP applies to the requests.  The `<img>` tag can be transformed
into a `cors` request by adding the `crossorigin` attribute:
```html
<img src="http://localhost:5005/photo.jpg"
    alt="Unable to load image" crossorigin/>
```
Now the CORP header no longer applies.