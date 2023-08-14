---
title: configuration
date: 2023-03-17T13:20:55-0600
draft: false
weight: 1
---
# [Configuration](https://gohugo.io/getting-started/configuration/)
Default configuration file is `hugo.toml`, `hugo.yaml`, or `hugo.json` in root of site.

```powershell
hugo --config filename.toml, … # generate a new config file(s)
```

## Configuration Directories
The configDir (ie: `config/`) can be used to store settings. Each file represents a configuration root object, so `params.toml` would contain:
```toml
[Params]
foo = 'bar'
```

Example structure:
```
├── config
│ ├── _default
│ │ ├── config.toml
│ │ ├── languages.toml
│ │ ├── menus.en.toml
│ │ ├── menus.zh.toml
│ │ └── params.toml
│ ├── production
│ │ ├── config.toml
│ │ └── params.toml
│ └── staging
│ ├── config.toml
│ └── params.toml
```

Hugo will merge all settings on to pof `config/_default/config.toml`. If running `hugo --environment staging`, all settings from `config/_default` will be merged with all those in `config/staging`.    

[List of all Configuration Settings](https://gohugo.io/getting-started/configuration/#all-configuration-settings)

## Configure Build
The build config section contains global build-related settings:
```toml
[build]
noJSConfigInAssets = false # enable if using VS Code; adds jsconfig.json to /assets
useResourceCacheWhen = 'fallback' # or never, always; when to use cached resources in /resources/_gen
writeStats = false # if true, creates hugo_stats.json at project root; used for CSS pruning
```

## Configure Server
The server config section only applies when running `hugo server` (development).  
This file can be placed under `config/development/server.toml`:
```toml
[[headers]]
for = '/'
[headers.values]
Content-Security-Policy = 'script-src localhost:1313'
Referrer-Policy = 'strict-origin-when-cross-origin'
X-Content-Type-Options = 'nosniff'
X-Frame-Options = 'DENY'
X-XSS-Protection = '1; mode=block'
```
If placed in root, change top of file from `[[headers]]` to
```toml
[server]
[[server.headers]]
```

If you add one or more directs to server config, add the 404 redirect explicitly, like this:
```toml
[[redirects]]
from = "/"
to = "/404.html"
status = 404
```
Sample Configuration File
```toml
baseURL = '<https://yoursite.example.com/>'
title = 'My Hugo Site'
[params]
AuthorName = 'Jon Doe'
GitHubUser = 'spf13'
ListOfFoo = ['foo1', 'foo2']
SidebarRecentLimit = 5
Subtitle = 'Hugo is Absurdly Fast!'
[permalinks]
posts = '/:year/:month/:title/'
```
