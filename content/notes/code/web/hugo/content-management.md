---
title: ""
date: 2023-01-01T00:00:00-06:00
draft: true
---

<style>
    r { color: red }
    o { color: orange }
    g { color: green }
</style>

# Overview
## Pretty URLs
By default, Hugo uses pretty URLs: `content/posts/blog/first-post.md` renders to `https://example.com/posts/blog/first-post/`.  
An ugly URL would be `https://example.com/posts/blog/first-post/index.html`.

# Content
```bash
.
└── content
    └── about
    |   └── index.md  // <- https://example.com/about/
    ├── posts
    |   ├── firstpost.md   // <- https://example.com/posts/firstpost/
    |   ├── happy
    |   |   └── ness.md  // <- https://example.com/posts/happy/ness/
    |   └── secondpost.md  // <- https://example.com/posts/secondpost/
    └── quote
        ├── first.md       // <- https://example.com/quote/first/
        └── second.md      // <- https://example.com/quote/second/
```
## Content type
*Content type* determines the *layout* and which *archtetype* template to use for the content.  

Hugo resolves content type from either:
- `type` in front matter, or, if not set
- the name of the top-level folder under `content/`

## Page Bundles
A *page bundle* groups pages and their resources.  It can either be a:
- *leaf bundle* (has no children)
- *branch bundle* (home page, section, taxonomy list, ...)

| | Leaf Bundle | Branch Bundle |
| 
### Leaf Bundle 
A directory at any level under `content/` that contains its own `index.md` file:
```bash
content/
├── about # leaf bundle
│   ├── index.md # WILL be rendered as its own page
├── posts # NOT a bundle
│   ├── my-post # leaf bundle
│   │   ├── content1.md # will NOT be rendered as its own page
│   │   ├── content2.md # will NOT be rendered as its own page
│   │   ├── image1.jpg
│   │   ├── image2.png
│   │   └── index.md # WILL be rendered as its own page
│   └── my-other-post # leaf bundle
│       └── index.md # WILL be rendered as its own page
│
└── another-section # NOT a bundle
    ├── ..
    └── not-a-leaf-bundle # NOT a bundle
        ├── ..
        └── another-leaf-bundle # leaf bundle
            └── index.md # WILL be rendered as its own page
```

### Branch Bundle
A directory at any level under `content/` that contains at least an `_index.md` file:
```bash
content/
├── branch-bundle-1 # branch bundle
│   ├── branch-content1.md
│   ├── branch-content2.md
│   ├── image1.jpg
│   ├── image2.png
│   └── _index.md
└── branch-bundle-2 # branch bundle
    ├── _index.md
    └── a-leaf-bundle # leaf bundle
        └── index.md
```

## Sections
Each top-level folder under `content/` is a *root section* as long as it is a *branch bundle*.
- *Leaf bundles* do not form their own sections.

Hugo automatically creates a page for each root section that lists all the content in that section.
- Section trees are navigable if at least the lower-most section has a content file (`_index.md`).
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

In this example, the sections are `blog`, `articles`, and `tutorials`:
```bash
├── content/
    ├── blog/
    ├── articles/
    └── tutorials/
```

## `_index.md`
- Specifies front matter and content for *list templates*.  
- Create one `_index.md` for homepage and one for each content section.

