---
title: notes > web > hugo > cli
date: 2023-05-01T00:00:00-06:00
draft: false
---

# hugo
Use `hugo` to deploy (publish) the site.  

| Options | Description |
|---------|-------------|
| --buildDrafts | build pages even if `draft: true` |
| --buildExpired | build pages even if expiry date is in the past |
| --buildFuture | build pages even if date is in the future |
| --destination /path/to/destination | publish the site to another destination |

# hugo server
use `hugo server` to develop and test the site.
| Options | Description |
|---------|-------------|
| --buildDrafts | build pages even if `draft: true` |
| --navigateToChanged | tell browser to automatically redirect to last modified page |
