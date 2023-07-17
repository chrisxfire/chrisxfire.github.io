---
title: notes > code > web > html > hyperlinks
date: 2023-04-26T17:22:15-0600
draft: false
weight: 1
---
# Overview
Links are defined with an `<a>` tag and the link's destination is assigned to the href *attribute*:
```html
<a href="https://www.w3schools.com">This is a link</a>
```

By default, an unvisited link is underlined/blue, visited is underlined/purple, active is underlined/red.

To use an image as a link, put the image inside the anchor tag:
```html
<a href="default.asp">
    <img src="smiley.gif" alt="HTML tutorial" style="width:42px;height:42px;">
</a>
```

# target attribute
Specifies where to open the linked document.
Values:
- `_self` — default
- `_blank` — new window/tab
- `_parent` — in parent frame
- `_top` — full body of current window

# Bookmarks
Bookmarks allow page visitors to jump to certain parts of the page.

Create a bookmark via the id attribute of an element:
```html
<h2 id="C4">Chapter 4</h2>
```

Link to the bookmark:
```html
<a href="#C4">Jump to Chapter 4</a>
<!-- or to the bookmark on another page: -->
<a href="html_demo.html#C4">Jump to Chapter 4</a>
```
