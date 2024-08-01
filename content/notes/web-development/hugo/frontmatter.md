---
title: frontmatter
date: 2023-05-01T00:00:00-06:00
draft: false
weight: 1
---

# Overview
Frontmatter (or *front matter*) is metadata for a page.

# Predefined Frontmatter
These predefined variables can be called from *Page Variables*.  This list is incomplete:
- `aliases` — an array of aliases that are published paths of renamed content that will be recreated in the output directory structure (see also: [Aliases](https://gohugo.io/content-management/urls/#aliases))
- `date` — the datetime assigned to this page
- `description` — a description of the page
- `draft` — if true, hugo will not publish unless `--buildDrafts` is passed
- `expiryDate` — if in the past, hugo will not publish unless `--buildExpired` is passed
- `images` — an array of paths to images related to this page
- `keywords` — the meta keywords for this content
- `lastmod` — the datetime at which content was last modified
- `linkTitle` — if set, Hugo defaults to using the `linkTitle` before the `title` (see also: [Order lists of content by linktitle](https://gohugo.io/templates/lists/#by-link-title))
- `outputs` — specify the output formats (see also: [Output formats](https://gohugo.io/templates/output-formats/))
- `publishDate` — if in the future, hugo will not publish unless `--buildFuture` is passed
- `slug` — overrides the last segment of the URL path (see also: [URL management](https://gohugo.io/content-management/urls/#slug))
- `type` — the type of the content; derived from the directory (the *section*) if nto specified here (see also: [Sections](https://gohugo.io/content-management/sections/))
- `url` — overrides the URL path; works for both regular pages and sections (see also: [URL management](https://gohugo.io/content-management/urls/#slug))
- `weight` — specify weight to order content in lists
  - lower weight comes first
  - must be non-zero
  - see also: [Ordering content in lists](https://gohugo.io/templates/lists/#order-content)

# User-defined Frontmatter
User-defined frontmatter fields can be added.  They are placed into a single .Params variable for use in templates.

Example:
```toml
include_toc = true
show_comments = false
```

The above fields can be accessed via `.Params.include_toc` and `Params.show_comments`.
