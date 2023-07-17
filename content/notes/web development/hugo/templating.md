---
title: notes > web development > hugo > templating
date: 2023-03-20T12:37:48-0600
draft: false
weight: 1
---
# Templating
Templating controls how a page is rendered. It uses variables, loops, conditions, and functions.

##  Params
Use to access a variable:
```html
<title>{{ .Params.title }}</title>
```

## Site
Use to access variables in `config.toml`:
```html
<title>{{ .Site.title }}</title>
```

## Conditions
```html
{{ if isset .Params "title" }}
    <title>{{ .Params.title }}</title>
{{ else }}
    <title>{{ .Site.title }}</title>
{{ end }}
```

## Variables
Set variables with $:
```css
{{ $favorite_food := "Gazelle" }}
{{ $favorite_food }}
```

## Looping
<!-- In Go, an array that can change size is called a slice.
You can iterate over an array or slice using range. -->
```html
{{ $best_friends := slice "pumbaa" "timon" "nala" "rafiki" }}

<ul>
    {{ range $best_friends }}
        <li>{{ . }}</li>
    {{ end }}
</ul>
```

# Footer Example
In `config.toml`:
```toml
[params]
name = 'Simba'

In `/layouts/partials/footer.html`:
{{ with .Params.hide_footer }}
<!-- No footer here! -->
{{ else }}
<footer>
Website made by {{ .Site.Params.name }} in {{ now.Year }}
</footer>
{{ end }}
```

Before `<body>` in `/layouts/_default/baseof.html`:
```css
{{ partial "footer.html" . }}
```

In `about.md`, toggle the footer in the front matter:
```
hide_footer:true
```
