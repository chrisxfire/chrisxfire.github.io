---
title: obsidian
date: 2024-06-10T00:00:00-06:00
draft: false
weight: 1
---

# Abstract
[Obsidian](https://obsidian.md) is a Markdown-powered note taking tool.

# Callouts
To create a callout, add `[!info]` to the first line of a blockquote, like so:  
```
> [!info] Here's a callout block.
> It supports **Markdown**, [[Wikilinks]], and [[Embedded files|embeds]].
> ![[Somefile.jpg]]
```

## Callout Types
There are the callout types and their aliases:
* `abstract` (`summary`, `tldr`)
* `info`
* `todo`
* `tip` (`hint`, `important`)
* `success` (`check`, `done`)
* `question` (`help`, `faq`)
* `warning` (`caution`, `attention`)
* `failure` (`fail`, `missing`)
* `danger` (`error`)
* `bug` 
* `example`
* `quote` (`cite`)

## Folding
Fallouts are made foldable by adding a `+` (expanded by default) or `-` (collapsed by default) after the type identifier:
```
> [!faq]- Foldable callout
> More info here.
```

## Nesting
Callouts can be nested:
```
> [!info] This callout has another nested in it.
> > [!faq] And here it is.
```

## Titles
The title of the callout is its type identifier by default. Change this by adding text after the type identifier:
```
> [!tip] Custom title
> Custom text.
```

# Diagrams

# Embedding Web Pages
To embed a web page:  
`<iframe src="https://www.example.com/"></iframe>`

To embed a YouTube video or a Tweet, use the Markdown syntax for external images:  
`![](https://www.youtube.com/watch?v=id)`

# Formatting
* `~~Strikethrough~~`  
* `==Highlight==`  
* `%% Comments`
* Horizontal rule `---`

# Footnotes
```
This is a footnote[^1].

This is another footnote[^fn].

[^1]: This is the referenced text.  
[^fn]: This referenced text spans multiple lines
  due to the two spaces at the beginning of this one.
```

# Images
* Link to images: `![Description](https://example.com/image.png)`
* Link to and resize an image: `![Description|100x150](https://example.com/image.png)`

# Linking
Obsidian supports WikiLink and Markdown links. The WikiLink format is shown below.
* Link to a note: `[[Note name]]`
* Link to a note with custom display text: `[[Note name|custom text here]]`
* Link to a note's heading: `[[Note name#Abstract]]`
* Link to a note in another vault: `[Note](obsidian://open?valut=ValutName&file=Note.md)`

## Link to a block in a note
In the note, add a block identifier:
```
This is some note. ^some-identifier
```

To link to the block:  
```
[[Note name#^some-identifier]]
```

## Embedding
To embed a note in another note, add an exclamation mark in front of an internal link:
```
![[Some note]]
```

### Embedding Files
The following files can be embedded:
* Markdown (md)
* Image (avif, bmp, gif, jpg, jpeg, png, svg, webp)
* Audio (flac, m4a, mp3, ogg, wav, webm, 3gp)
* Video (mkv, mov, mp4, ogv, webm)
* PDF (pdf)

Files are embedded just like notes:
```
![[filename.ext]]
```

# Math Expressions
Obsidian supports math expressions via [MathJax](https://docs.mathjax.org/en/latest/basic/mathjax.htm) and LaTeX.

Create a multi-line math expression:
```
$$
\begin{vmatrix}a & b\\
c & d
\end{vmatrix}=ad-bc
$$
```

Create an inline math expression: `$e^{2i\pi} = 1$`

# Tags
Tags can be used as keywords or topics for notes. 
* Tag names can include alphanumeric characters, underscore, and hyphen. 
* They must contain at least one non-numeric character.
* Tags are case-insensitive.

## Creating Tags
Tags are created like so: `#meeting`

Tags can also be created with the `tags` property in frontmatter:
```
---
tags:
 - meeting
 - boring
---
```

Tags can be searched using the `tag:` search operator.

## Nested Tags
Tags can be nested like so: `#inbox/to-process`

# Tasks
A line can be marked as a task with <kbd>Ctrl</kbd> + <kbd>L</kbd>.  
Tasks can be searched via `task-todo:<search term>` for open tasks and `task-done:<search term>` for closed tasks.

## Task Plugin
Documentation: [Introduction - Tasks User Guide - Obsidian Publish](https://publish.obsidian.md/tasks/Introduction)