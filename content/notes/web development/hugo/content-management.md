---
title: notes > web development > hugo > content management
date: 2023-05-01T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Credit: [Cloud Cannon](https://cloudcannon.com/blog/the-ultimate-guide-to-hugo-sections/)  
## Pretty URLs
By default, Hugo uses pretty URLs: `content/posts/blog/first-post.md` renders to `https://example.com/posts/blog/first-post/`.  
An ugly URL would be `https://example.com/posts/blog/first-post/index.html`.

# Content
If a directory has an `_index.md`, Hugo uses it to create a listing of files/directories underneath that directory.  

Without any further configuration, this works:
```bash
.
└── content
    └── about
    |   └── index.md  # <- https://example.com/about/
    ├── posts
    |   ├── firstpost.md   # <- https://example.com/posts/firstpost/
    |   ├── happy
    |   |   └── ness.md  # <- https://example.com/posts/happy/ness/
    |   └── secondpost.md  # <- https://example.com/posts/secondpost/
    └── quote
        ├── first.md       # <- https://example.com/quote/first/
        └── second.md      # <- https://example.com/quote/second/
```
## Content type
*Content type* determines the *layout* and which *archtetype* template to use for the content.  

Hugo resolves content type from either:
- `type` in front matter, or, if this is not set:
- the name of the top-level folder under `content/`
  - for example, `content/about-us/_index.md` has a `type` of `about-us`

## Page Bundles
A *page bundle* groups pages and their resources.  It can either be a:
- *leaf bundle* (has no children)
- *branch bundle* (home page, section, taxonomy list, ...)

### Leaf Bundle 
Directories at any level under `content` that have an `index.md` file.
- They have a layout type of `single` (`layouts/_default/single.html` is assigned as its template).
- They can never be *sections*.
- Any additional `.md` files in the leaf bundle <o>will not</o> get their own navigable URL.

```bash
.
└── content
    └── product1 # Leaf bundle
        └── index.md # navigable at example.com/product1
        └── prod1_brochure_large.pdf
        └── prod1_brochure_small.pdf
        └── prod1_hero_img.jpg
        └── prod1_users_img1.jpg
        └── prod1_users_img2.jpg
        └── prod1_users_img3.jpg
        └── somefile.md # will NOT be rendered with its own navigable URL
```

### Branch Bundle
Branch bundles are directories at any level under `content/` that have an `_index.md` file.
- They have a layout type of `list` (`layouts/_default/list.html` is assigned as its template). 
- They are always *sections*.
- Any additional `.md` files in the branch bundle get their own navigable URL.

```bash
.
└── content
    └── product2
        └── _index.md # this makes content/product2 a branch bundle
        └── awards
            └── 2020.md # navigable at example.com/product2/awards/2020
            └── 2021.md
            └── 2022.md
        └── brochures
            └── index.md # navigable at example.com/product2/brochures
            └── prod2_brochure_large.pdf
            └── prod2_brochure_small.pdf
        └── extended-warranty.md # navigable at example.com/product2/extended-warranty
        └── images
            └── prod2_awards_img.jpg
            └── prod2_ext-warr_img.jpg
            └── prod2_hero_img.jpg
            └── prod2_users_img1.jpg
            └── prod2_users_img2.jpg
            └── prod2_users_img3.jpg
```

## Sections
Hugo automatically creates a page for both *root sections* and *nested sections* that lists all the content in that section.  

### Root Sections
Each top-level folder under `content/` is a *root section*.  
In this example, the root sections are `blog`, `articles`, and `tutorials`:
```bash
├── content/
    ├── blog/
    ├── articles/
    └── tutorials/
```

### Nested Sections
Under `content/`, each folder is a *nested section* as long as it also contains `_index.md`.  
- *Leaf bundles* do <o>not</o> form their own sections because they do not have `_index.md` (only `index.md)`).

```bash
content/
└── blog/                   # <-- Section, because first-level dir under content/
    ├── funny-cats/
    │   ├── mypost.md
    │   └── kittens/        # <-- Section, because contains _index.md
    │       └── _index.md
    └── tech/               # <-- Section, because contains _index.md
        └── _index.md
```

Consider:
```bash
.
└── content/
    └── about-us/
        └── leadership
```
Since `content/about-us` *is* a section, either of the following result in a single page at `example.com/about-us/leadership`:
- content/about-us/leadership/index.md
- content/about-us/leadership.md

## `_index.md`
- Specifies front matter and content for *list templates*.  
- Create one `_index.md` for homepage and one for each content section.

## Templates
- `layouts/index.html` for the site's home page (falls back to `layouts/_default/single.html`)
- `layouts/_default/single.html` for any `index.md`
- `layouts/_default/list.html` for any `_index.md`

```bash
.
└── content
    └── about-us 
        └── _index.md # layouts/_default/list.html
        └── company-history.md # layouts/_default/single.html
        └── office-locations.md # layouts/_default/single.html
    └── support 
        └── index.md # layouts/_default/single.html
```
