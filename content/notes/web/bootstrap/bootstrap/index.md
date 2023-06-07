---
title: notes > web > bootstrap > bootstrap
date: 2023-04-27T11:05:24-0600
draft: true
---
# Overview
An open-source, front-end web development framework.
Uses HTML, CSS, JavaScript.
Download bootstrap ([www.getbootstrap.com](http://www.getbootstrap.com)) or use a Bootstrap 5 CDN:
`<head>`
`<!-- Latest compiled and minified CSS -->`
`<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css" rel="stylesheet">`

`<!-- Latest compiled JavaScript -->`
`<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.bundle.min.js"></script>`
`</head>`

# Basic Bootstrap 5 Page
`<!DOCTYPE html>`
`<html lang="en">`
`<head>`
`<title>Bootstrap Example</title>`
`<meta charset="utf-8">`
`<meta name="viewport" content="width=device-width, initial-scale=1">`
`<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/css/bootstrap.min.css" rel="stylesheet">`
`<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.2.3/dist/js/bootstrap.bundle.min.js"></script>`
`</head>`
`<body>`

`<div class="container">`
`<h1>My First Bootstrap Page</h1>`
`<p>This part is inside a .container class.</p>`
`<p>The .container class provides a responsive fixed width container.</p>`
`</div>`

`</body>`
`</html>`

# Concepts
Layout — bootstrap uses a grid layout system
Components — building blocks with styling already applied
Interactivity — via JavaScript
Style utilities — margins, padding, alignment, etc
Themes

# Downloading Bootstrap
bootstrap/
css/ — Bootstrap CSS library (`bootstrap.css`) and all of its individual components
js/ — Bootstrap JavaScript library (`bootstrap.js`) and with the Popper library (`bootstrap.bundle.js)`
