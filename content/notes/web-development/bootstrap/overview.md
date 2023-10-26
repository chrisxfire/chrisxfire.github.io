---
title: overview
date: 2023-04-27T11:05:24-0600
draft: false
weight: -1
---

# Overview
- An open-source, front-end web development toolkit.  Uses HTML, CSS, JavaScript
- Bootstrap uses Popper for dropdowns, popovers and tooltips
- Compare to [W3.CSS](../../css/w3-css/overview)
- Documentation: https://getbootstrap.com/docs/5.3  

# Getting Started
## Installation
Prefer LibMan over NuGet:  
```sh
libman install bootstrap
libman install bootstrap.sass
```

## A Basic Bootstrap 5 `index.html`
1. Create an `index.html` file with a `<meta>` tag's `name` attribute set to "viewport" to enable responsive behavior:
```html
<!-- Bootstrap requires this HTML5 doctype: -->
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <!-- ... -->
```
2. In the `<head>` tag, add a `<link>` tag for Bootstrap's CSS:
```html
<!doctype html>
<html lang="en">
  <head>
    <!-- ... -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" 
          rel="stylesheet" 
          integrity="sha384-9ndCyUaIbzAi2FUVXJi0CjmCapSmO7SnpJef0486qhLnuZ2cdeRhO02iuK6FUUVM" 
          crossorigin="anonymous">
  </head>
  <!-- ... -->
```
3. In the `<body>`, add a `<script>` for Bootstrap's JavaScript bundle.  This bundle includes both JavaScript and Popper:
```html
<!-- ... -->
    <body>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js" 
            integrity="sha384-geWF76RCwLtnZ8qwWowPQNguL3RmwHVBC9FhGdlKrxdiJJigb/j/68SIy3Te4Bkz" 
            crossorigin="anonymous"></script>
  </body>
<!-- ... -->
```
4. Optionally, add Popper (for dropdowns, popovers and tooltips) and JavaScript separately:
```html
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.11.8/dist/umd/popper.min.js" 
        integrity="sha384-I7E8VVD/ismYTF4hNIPjVp/Zjvgyol6VFvRkX/vR+Vc4jQkC+hVqc2pM8ODewa9r" 
        crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.min.js" 
        integrity="sha384-fbbOQedDUMZZ5KreZpsbe1LCZPVmfTnH7ois6mU1QK+m14rQ1l2bGBq41eYeM/fS" 
        crossorigin="anonymous"></script>
```

# Bootstrap Components that Require JavaScript
- Alerts
- Buttons
- Carousel
- Collapse
- Dropdowns (+Popper)
- Modals
- Navbar
- Navs with Tab plugin
- Offcanvas's
- Scrollspy
- Toasts
- Tooltips (+Popper)
