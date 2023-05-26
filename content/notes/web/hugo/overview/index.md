---
title: "notes > web > hugo > overview"
date: 2023-05-01T00:00:00-06:00
draft: false
---

# Overview
Hugo is a static site generator.  
2 editions: *Standard* and *Extended* (includes encoding WebP images, transposing Sass to CSS)

## Installation
`winget install hugo.hugo.extended`

Test the installation:  `hugo version`

## Getting Help
`hugo help`
`hugo command --help`

## Generate a Site
`hugo new site example`

This creates:
```bash
example/
├── archetypes/
│   └── default.md
├── assets/ # all the files which need to be processed by Hugo Pipes (Hugo's asset processing engine)
├── content/
├── data/
├── layouts/
├── public/
├── static/
├── themes/
└── config.toml # could be /config if you have a large number of configuration directives
```

### Build & Publish the site
`hugo`

This builds the site and publishes the files to `/public`.  This includes HTML and assets (images, CSS, JS, etc).
- Hugo does not clear `/public` before building the site.

The structure for `/public`:
```bash
public/
├── categories/
│   ├── index.html
│   └── index.xml  # <-- RSS feed for this section
├── post/
│   ├── my-first-post/
│   │   └── index.html
│   ├── index.html
│   └── index.xml  # <-- RSS feed for this section
├── tags/
│   ├── index.html
│   └── index.xml  # <-- RSS feed for this section
├── index.html
├── index.xml      # <-- RSS feed for the site
└── sitemap.xml
```
### Build and publish to a different location
`hugo --destination /path/to/destination`

### Build a Test Site
`hugo server`
`hugo server --navigateToChanged` (The browser will automatically redirect to content when it is changed)

# Customization
## Customizing the width of posts
Adjust `$narrow-size` and `$spacing-full` in `/assets/sass/main.scss`