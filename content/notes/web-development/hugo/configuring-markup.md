---
title: configuring markup
date: 2023-03-17T13:21:01-0600
draft: false
weight: 1
---
# [Configuring Markup](https://gohugo.io/getting-started/configuration-markup/)
All markup related settings and their defaults:
```toml
[markup]
defaultMarkdownHandler = 'goldmark'

[markup.asciidocExt]
backend = 'html5'
extensions = []
failureLevel = 'fatal'
noHeaderOrFooter = true
preserveTOC = false
safeMode = 'unsafe'
sectionNumbers = false
trace = false
verbose = false
workingFolderCurrent = false

[markup.asciidocExt.attributes]

[markup.goldmark]

[markup.goldmark.extensions]
definitionList = true
footnote = true
linkify = true
linkifyProtocol = 'https'
strikethrough = true
table = true
taskList = true
typographer = true

[markup.goldmark.parser]
autoHeadingID = true
autoHeadingIDType = 'github'
wrapStandAloneImageWithinParagraph = true

[markup.goldmark.parser.attribute]
block = false
title = true

[markup.goldmark.renderer]
hardWraps = false
unsafe = false
xhtml = false

[markup.highlight]
anchorLineNos = false
codeFences = true
guessSyntax = false
hl_Lines = ''
hl_inline = false
lineAnchors = ''
lineNoStart = 1
lineNos = false
lineNumbersInTable = true
noClasses = true
noHl = false
style = 'monokai'
tabWidth = 4

[markup.tableOfContents]
endLevel = 3
ordered = false
startLevel = 2
```
