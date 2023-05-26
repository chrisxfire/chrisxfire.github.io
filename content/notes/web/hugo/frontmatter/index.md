---
title: "notes > web > hugo > frontmatter"
date: 2023-05-01T00:00:00-06:00
draft: false
---

# Frontmatter
## Content Frontmatter
- `draft` (if true, hugo will not publish)
- `date` (if in the future, hugo will not publish)
- `publishDate` (if in the future, hugo will not publish)
- `expiryDate` (if in the past, hugo will not publish)

Override the frontmatter with:  
`hugo --buildDrafts` or `--buildExpired` or `--buildFuture`