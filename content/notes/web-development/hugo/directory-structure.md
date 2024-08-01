---
title: directory structure
date: 2023-03-17T13:20:38-0600
draft: false
weight: 1
---
# [Directory Structure](https://gohugo.io/getting-started/directory-structure/)
Scaffolds a project directory structure and takes a single directory and uses it as the input to create a website.

hugo new site creates:
```
example/
├── archetypes/
│ └── default.md
├── assets/
├── content/
├── data/
├── layouts/
├── public/
├── static/
├── themes/
└── config.toml
```
## [archetypes](https://gohugo.io/content-management/archetypes/)
hugo creates new content files with `date`, `title`, and `draft = true` frontmatter.

## [assets](https://gohugo.io/hugo-pipes/introduction#asset-directory)
All the files which need to be processed by Hugo Pipes.  
Files whose `.Permalink` or `.RelPermalink` are used are published in publish directory.

## [config](https://gohugo.io/getting-started/configuration/)
Stores configuration directives as JSON, YAML or TOML.  
A single `config.toml` at the project root can be used if desired.

## [content](https://gohugo.io/content-management/organization/)
Sites content (like blog, articles, tutorials) is broken up into subdirectories under `/content`.  
These sections assign default *content types.*

## [data](https://gohugo.io/templates/data-templates/)
Configuration files that are used to generate a website in YAML, JSON or TOML format.  
Also contains *data templates* that pull from dynamic content.

## [layouts](https://gohugo.io/templates/)
Templates as `.html` files for views of content. Includes list pages, homepage, taxonomy templates, partials, single page templates, others.

## [static](https://gohugo.io/content-management/static-files/)
Images, CSS, JavaScript. Assets in `/static` are copied over as-is when hugo builds the site.

## [resources](https://gohugo.io/getting-started/configuration/#configure-file-caches)
Stores caches of some files to speed up generation.

## public
Directory structure:
```
public/
├── categories/
│ ├── index.html
│ └── index.xml <-- RSS feed for this section
├── post/
│ ├── my-first-post/
│ │ └── index.html
│ ├── index.html
│ └── index.xml <-- RSS feed for this section
├── tags/
│ ├── index.html
│ └── index.xml <-- RSS feed for this section
├── index.html
├── index.xml <-- RSS feed for the site
└── sitemap.xml
```
