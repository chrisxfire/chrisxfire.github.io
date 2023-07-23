---
title: notes > asp.net > web apps > blazor > components > navlink and navmenu components
date: 2023-07-18T00:00:00-06:00
draft: false
weight: 1
---

# NavLink
Use a `NavLink` component in place of HTML hyperlink elements (`<a>`) for navigation links.  A `NavLink` component toggles an `active` CSS class to help a user understand which page is active among the navigation links.

Optionally, assign a CSS class name to `NavLink.ActiveClass` to apply a custom CSS class to the rendered link when the current route matches.

Any attributes not defined by the component are passed through to the anchor element, like this `target` attribute:
```html
<NavLink href="example-page" target="_blank">Example page</NavLink>
```

...renders as...
```html
<a href="example-page" target="_blank">Example page</a>
```

## Match attribute
`NavLink`'s Match attribute can be assigned either:
1. `NavLinkMatch.All`—the `NavLink` is active when it matches the *entire* current URL
2. `NavLinkMatch.Prefix` (default)—the `NavLink` is active when it matches any prefix of the current URL
