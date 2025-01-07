---
title: cross origin embedder policy
date: 2025-01-06T00:00:00-06:00
draft: false
weight: 1
tags:
 - kb/web-dev/security/cross-origin-security-headers
---

# [`Cross-Origin-Embedder-Policy` (COEP) to secure embedded resources](https://andrewlock.net/understanding-security-headers-part-3-cross-origin-embedder-policy/)
CORP headers prevent resources on a site from being embedded across origins. COEP headers declare that the site will *only* load resources that 
have opted-in to being loaded across origins.

## motivation
COEP headers work in conjunction with CORP headers to prevent cross-site script inclusion (XSSI) attacks. Additionally, certain JavaScript 
features like `SharedArrayBuffer`, `performance.measureUserAgentSpecificMemory()` or high-precision timers require the use of COEP headers.

## `Cross-Origin-Embedder-Policy`
The `Cross-Origin-Embedder-Policy` header has three possible values:
1. `unsafe-none` — the default value.
2. `require-corp` — the most restrictive value; requires that all cross-origin requests either:
	1. Include a CORP header (for `no-cors` requests), or
	2. Include a `Access-Control-Allow-Origin` header (for `cors` requests).
3. `credentialless` — an intermediate value; no requirements for CORP or ACAO headers, but `no-cors` cross-origin requests are sent without cookies and no cookies are saved from the response.

## COEP, CORP and CORS
Consider this link to an image:
```html
<img src="https://example.com/photo.jpg" />
```

This is a `no-cors` request for an image. It is typically allowed without issue. Recall that CORP headers enforce that only `same-origin` or
`same-site` resources can be accessed by a document. In contrast, cross-origin requests using `fetch()` are typically `cors` requests. The
request for an image above can be transformed into a `cors` request:
```html
<img src="https://example.com/photo.jpg" crossorigin/>
```

If the COEP header is set to `require-corp`, then:
- `no-cors` requests:
	- Must return a CORP header value that indicates the resource is allowed to be accessed:
		- If the CORP header value is `same-origin`, then the embedded resource can only be loaded if it has the same origin as the COEP document.
		- If the CORP header value is `same-site`, then the embedded resources can only be loaded if it has the same site as the COEP document.
		- If the CORP header value is `cross-origin`, then the embedded resource can be loaded in any embedded document.
- `cors` requests:
	- Must return a CORS header value (an ACAO header) that indicates the resource is allowed to be accessed.

## details about `credentialless`
Using `require-corp` is cumbersome. See [this article](https://web.dev/articles/coop-coep#2_ensure_resources_have_corp_or_cors_enabled) for all the steps 
involved. 

One particular restriction is that, for resources that (1) you don't control, (2) are not sent with a CORP header, and (3) are not
CORS enabled, there's no way (that you control) to embed the resources. The `credentialless` value was created to address this. When using
`credentialless`:
1. The site is still considered cross-origin isolated (and features like `SharedArrayBuffer` will work)
2. `no-cors` requests do *not* need to have a `Cross-Origin-Resource-Policy` to be embeded into the site.

Note that if the embedded resource *does* return a CORP header, it will still be honored, and the resource cannot be embedded to your site.