---
title: notes > code > web > hugo > layouts, styles, partials
date: 2023-03-20T12:37:30-0600
draft: false
---
# Layouts
*Content* is purely the content of a page and expressed in Markdown.  
Layouts are the "framing" of a page (header, footer, etc) and the formatting of the *content*.  

Content pages use the `single` layout by default.  
A content page named `_index.html` uses the `list` layout.  

Hugo uses [this lookup order](https://gohugo.io/templates/lookup-order/) to determine which layout to use. The last place it checks is `/layouts/_default`.

## Baseof
Create `/layouts/_default/baseof.html`:
```html
<!doctypehtml>
<html>
<head>
<metacharset="utf-8">
<title>{{ .Page.Title }}</title>
</head>

<body>
{{ block "main" . }}
{{ end }}
</body>
</html>
```

The main block is a placeholder that other layouts can use to define only that part of the page. Another layout, like `/layouts/_default/someLayout.html`, can access it like this:
```css
{{ define "main" }}
{{ .Content }}
{{ end }}
```

## Styles
Hugo uses SASS (Syntactically Awesome Stylesheets), an extension to CSS. Sass gets processed into a CSS file.
SASS usually lives in `.scss` files in `/assets/sass`.

### Referencing a Style Sheet in a Layout
```css
{{ $style := resources.Get "sass/main.scss" | resources.ToCSS | resources.Minify }}
<linkrel="stylesheet"href="{{ $style.Permalink }}">
```

## Partials
Partials are files that can be included in a layout to reduce repetition or complexity.
They usually live in `/layouts/partials`.

### Nav Bar example
Create `/layouts/partials/nav.html`:
```html
<nav>
<ul>
<li><ahref="/">Home</a></li>
<li><ahref="/about/">About</a></li>
</ul>
</nav>
```
In `/layouts/_default/baseof.html` below `<body>`:
```css
{{ partial "nav.html" }}
```