---
title: cross origin opener policy
date: 2025-01-06T00:00:00-06:00
draft: true
weight: 1
tags:
 - kb/web-dev/security/cross-origin-security-headers
---

# [`Cross-Origin-Opener-Policy` (COOP) to prevent attacks from popups](https://andrewlock.net/understanding-security-headers-part-1-cross-origin-opener-policy-preventing-attacks-from-popups/)
## origins
An *origin* is a URL from the browser's point of view. Two URLs have the same origin if the following components of the URL match:
- the scheme (i.e.: `http` or `https`)
- the TLD (`.com`)
- the domain (`example.com`)
- the subdomain (`www.`)
- the port

Notably, paths (`/some/path`) and querystrings (`?key=value`) and fragments (`#someid`) are not part of the origin.

## [`same-origin` policy](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy)
The same-origin policy is a security mechanism used by browsers to restrict how resources loaded from one orgin can interact with
resources loaded from another. This is why cross-origin requests are blocked unless Corss Origin Resource Sharing (CORS) is enabled.

Aside from `fetch()`, there are other JavaScript APIs that interact with different documents, like `iframe.contentWindow` (which returns 
the `Window` object of an iFrame). If documents are of the same-origin, then you have direct access to the other `Window`. But if they
are not, you can only access [a limited number of properties and methods](https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy#window) 
of the `Window`. Despite this restriction, there are still attacks that use these APIs to leak information across origins.

## vulnerabilities
Cross-site leaks ("[XS-Leaks](https://xsleaks.dev/)") attack the side-channels built into web platforms to infer information about other sites.
For example, `window.Length` returns the number of `iframe`s in a document. Consider a scenario where this number changes based on the properties
of the user. This would make it a property that can be abused. Facebook [patched a bug](https://www.imperva.com/blog/facebook-privacy-bug/) that
abused this property.

### `Cross-Origin-Opener-Policy`
`Cross-Origin-Opener-Policy` is a security header that can be returned in HTTP responses which enables additional protections for when different documents
call `window.open` on your site. It has three possible values:
1. `unsafe-none` — the default (unsafe) value
2. `same-origin` — the most safe value
3. `same-origin-allow-popups` — a middle ground

Consider two different sites: 
- The *opener* calls `window.Open()` which returns a `Window` object that references the *opened* site. 
- The *opened* site can use the `window.opener` property to reference the `Window` object of the *opener*. 

Both sites can set different values for COOP. The combination of the two values controls whether or not the two documents are in the same [browsing context](https://developer.mozilla.org/en-US/docs/Glossary/Browsing_context).
If they are in different browsing contexts, then:
- In the opened, `window.opener` is `null`.
- in the opener, `window.open()` returns "default" values for some properties.

#### scenarios
Consider two web apps:
1. Serves an `Index.html` that contains a button which returns `window.open()` in open a popup in #2.
2. Serves a `Popup.html` which attempts to read `window.opener`.

> Scenario 1
- Both apps have the same origin.
- Result:
	- The `Cross-Origin-Opener-Policy` on either app is ignored.
	- In the opener: `window.closed` returns `false` (the correct value).
	- In the opened: `window.opener` returns the "real" `Window` object.

> Scenario 2
This scenario is the least secure.

- The apps have different origins.
- Both apps set `Cross-Origin-Opener-Policy: unsafe-none` (or don't set the header at all).
- Result:
	- `window.opener` is available in the popup.
	- In the opener: `window.closed` returns `false` (the correct value).
	- In the opened: `window.opener` returns the real `Window` object.

> Scenario 3
This scenario is the most secure.

- The apps have different origins.
- One of the apps sets `Cross-Origin-Opener-Policy: same-origin`.
- Result:
	- In the opener: `window.closed` returns `true` (the incorrect value).
	- In the opened: `window.opener` retruns `null`.

When either app uses `same-origin`, that app opts out of context sharing, and without context sharing, the result is the same regardless of which app opts out.

> Scenario 4
- The apps have different origins.
- One of the apps sets `Cross-Origin-Opener-Policy: same-origin-allow-popups`.
- Result:
	- If the opener uses `unsafe-none` (or omits the header), the apps share browsing context.
	- If the opener uses anything else, the browsing contexts are isolated.
	- If the opened uses `unsafe-none`, the browsing contexts are isolated.

Summary of scenarios:
| Opener COOP value          | Opened COOP value          | Context is... |
|----------------------------|----------------------------|---------------|
| `unsafe-none` / missing    | `unsafe-none` / missing    | Shared        |
| `unsafe-none` / missing    | `same-origin-allow-popups` | Isolated      |
| `unsafe-none` / missing    | `same-origin`              | Isolated      |
| `same-origin-allow-popups` | `unsafe-none` / missing    | Shared        |
| `same-origin-allow-popups` | `same-origin-allow-popups` | Isolated      |
| `same-origin-allow-popups` | `same-origin`              | Isolated      |
| `same-origin`              | `unsafe-none` / missing    | Isolated      |
| `same-origin`              | `same-origin-allow-popups` | Isolated      |
| `same-origin`              | `same-origin`              | Isolated      |

### `Cross-Origin-Opener-Policy-Report-Only`
This header "simulates" the COOP policy and sends any violations via the browser's [reporting API](https://web.dev/reporting-api).
