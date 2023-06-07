---
title: notes > web > github pages > jekyll
date: 2022-12-21T00:00:00-07:00
draft: false
---

# Overview
GitHub pages uses Jekyll as its static site generator.

Some configuration settings cannot be changed for GitHub Pages:
```yaml
lsi: false
safe: true
source: [your repo's top level directory]
incremental: false
highlighter: rouge
gist:
  noscript: false
kramdown:
  math_engine: mathjax
  syntax_highlighter: rouge
```

# Custom Variables
Set custom variables that can be accessed in Liquid:
```
---
food: Pizza
---

<h1>{{ page.Food }}</ht1>
```

# Themes
GitHub Pages support Jekyll themes.
- Built-in themes
- Jekyll theme documentation

In `_config.yml`:  
```yaml
theme: theme-name
```

If `theme-name` is not a built-in theme, then it is in the format specified in that theme's README in its repository (usually user/repo).

# Create a GitHub Site with Jekyll
1. Create a GitHub Pages site > Navigate to the publishing source > `git rm -rf .` > `jekyll new --skip-bundle .`
2. Jekyll created a Gemfile.  Open it.  Prepend line that starts with `gem "jekyll"` with `#`
3. Change the line that starts with `# gem "github-pages"` 
to `gem "github-pages", "~> GITHUB-PAGES-VERSION", group: :jekyll_plugins`
Find the GITHUB-PAGES-VERSION here: https://pages.github.com/versions/
1. Save and close Gemfile
2. `bundle install`
3. Configure `_config.yml`:  
    ```yaml
    domain: my-site.github.io       # if you want to force HTTPS, specify the domain without the http at the start, e.g. example.com
    url: https://my-site.github.io  # the base hostname and protocol for your site, e.g. http://example.com
    baseurl: /REPOSITORY-NAME/      # place folder name if the site is served in a subfolder
    ```
4. `git add .`
5. `git commit -m 'Initial commit'`
6. `git remote add origin https://github.com/user/repository.git`
7.  `git push -u origin branch`
	
# Add Content to Jekyll Site
Two types of content:
1. Pages (like an "About" page)
2. Posts

Use the default about.md file as a template for other pages.

## Add a New Page
1. Navigate to repo > Navigate to publishing source > create new file page-name.md
2. Add the front matter:
    ```yaml
	layout: page
	title: "PAGE-TITLE"
	permalink: /URL-PATH
    ```
3. Add content
4. Commit

## Add a New Post
1. Navigate to repo > Navigate to publishing source > Navigate to _posts > create new file YYYY-MM-DD-name-of-post.md
1. Add the frontmatter:
    ```yaml
	layout: post
	title: "POST-TITLE"
	date: YYYY-MM-DD hh:mm:ss -0000
	categories: CATEGORY-1 CATEGORY-2
    ```
2. Add content
3. Commit
