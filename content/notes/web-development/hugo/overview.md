---
title: overview
date: 2023-05-01T00:00:00-06:00
draft: false
weight: -1
---

# abstract
Hugo is a static site generator.  
2 editions: *Standard* and *Extended* (includes encoding WebP images, transposing Sass to CSS)

## installation
`winget install hugo.hugo.extended`

Test the installation:  `hugo version`

## getting help
`hugo help`
`hugo command --help`

## generate a site
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
### build and publish to a different location
`hugo --destination /path/to/destination`

### build a test site
`hugo server`
`hugo server --navigateToChanged` (The browser will automatically redirect to content when it is changed)

# customization
## change syntax highlighting style
See https://xyproto.github.io/splash/docs/all.html for availble styles.

1. Navigate to `/themes/hugo-blog-awesome/assets`
2. Run `hugo gen chromastyles --style=<style-name> > code-highlight.css`

## customizing the width of posts
Adjust `$narrow-size` and `$spacing-full` in `/assets/sass/main.scss`
