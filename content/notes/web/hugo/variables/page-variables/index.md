---
title: notes > web > hugo > variables > page variables
date: 2023-06-18T00:00:00-06:00
draft: false
---

# Overview
Page-level variables are defined in the content's frontmatter, derived from the content's file location, or extract from the content body itself.

# Predefined Page Variables
All of the fields listed in [frontmatter](../frontmatter/index.md) are page variables in the format `.FieldName`.  Only page variables that are not listed on the [frontmatter](../frontmatter/index.md) notes page are listed here:
- `.AlternativeOutputFormats` — used for a page's `link rel` list in the site's `<head>` (see also: [Output formats(https://gohugo.io/templates/output-formats/)]
- `.Ancestors` — used to implement [breadcrumb navigation](https://gohugo.io/content-management/sections#example-breadcrumb-navigation)
- `.BundleType` — `leaf`, `branch`, or emtpy string if not a bundle
- `.Content` — the content itself which is defined below the frontmatter
- `.Data` — the data specific to this type of page
- `.File` — filesystem-related data (see also: [File variables](https://gohugo.io/variables/files/))
- `.Fragments` — fragments for this page (see also: [Fragments](https://gohugo.io/variables/page/#page-fragments))
- `.FuzzyWordCount` — approximate word count for the content of this page (see also: `.WordCount`)
- `.IsHome` — boolean if this is the homepage
- `.IsNode` — always `false` for regular content pages
- `.IsPage` — always `true` for regular content pages
- `.IsSection` — boolean if `.Kind` is `section`
- `.Kind` — the page's *kind* (`page`, `home`, `section`, `taxonomy`, `term`)
- `.Next` — points to the next *regular page* (a *post* page or a *content* page)
- `.NextInSection` — points to the next *regular page* below the same top level section (like `/blog`)
- `.Pages` — a collection of associated pages
- `.Plain` — the Page content stripped of HTML tags and returned as a string
- `.PlainWords` — a slice of strings that results from splitting `.Plain` into words
- `.Prev` — points down to the previous *regular page*
- `.PrevInSection` — points down to the previous *regular page* below the same top level section (like `/blog`)
- `.RawContent` — raw markdown content without the frontmatter
- `.ReadingTime` — the estimated time, in minutes, it takes to read teh content
- `.Site` — see [Site Variables](https://gohugo.io/variables/site/)
- `.Summary` — a generated summary of the content (see also: [Content summaries](https://gohugo.io/content-management/summaries/))
- `.TableOfContents` — a generated [table of contents](https://gohugo.io/content-management/toc/) for this page
- `.Truncated` — boolean if the `.Summary` is truncated (useful for showing a "read more" link)
- `.WordCount` — the number of words in the content

# Section Variables and Methods
- `.CurrentSection` — the page's current section (the page itself if it is a section or homepage)
- `.FirstSection` — the page's first section below root (like `/docs` or `/blog`)
- `.InSection $anotherPage` — boolean if `$anotherPage` is in the current section
- `.IsAncestor $anotherPage` — boolean if the current page is an ancestor of `$anotherPage`
- `.IsDescendant $anotherPage` — boolean if the current page is a descendant of `$anotherPage`
- `.Parent` — 
  - if this page is a *section*, returns the parent section
  - if this is a *regular page*, returns its *section*
- `.Section` — the *section* this content belongs to
- `.Sections` — the sections below this content

# See Also
- [The .Pages Variable](https://gohugo.io/variables/page/#pages)
- [Page Fragments](https://gohugo.io/variables/page/#page-fragments)
- [The glboal page function](https://gohugo.io/variables/page/#the-global-page-function)
- [Page-level Params](https://gohugo.io/variables/page/#page-level-params)