---
title: hosting
date: 2023-03-17T13:34:53-0600
draft: false
weight: 1
---

# [GitHub](https://gohugo.io/hosting-and-deployment/hosting-on-github/)
1.  Create GitHub repo
2.  Push local repo to GitHub
3.  From GitHub repo > **Settings** > **Pages** > **Build and deployment** > Source = GitHub Actions
4.  Create `.github/workflows/hugo.yaml` file in local repo:

# sample workflow for building and deploying a hugo site to github pages
```yaml
name: Deploy Hugo site to Pages

on:
# runs on pushes targeting the default branch
push:
branches:
- main

# allows you to run this workflow manually from the actions tab
workflow_dispatch:

# sets permissions of the github_token to allow deployment to github pages
permissions:
contents: read
pages: write
id-token: write

# allow one concurrent deployment
concurrency:
group: "pages"
cancel-in-progress: true

# default to bash
defaults:
run:
shell: bash

jobs:
# build job
build:
runs-on: ubuntu-latest
env:
HUGO_VERSION: 0.111.2
steps:
- name: Install Hugo CLI
run: |
    wget -O ${{ runner.temp }}/hugo.deb [https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_extended_${HUGO_VERSION}_linux-amd64.deb](https://github.com/gohugoio/hugo/releases/download/v$%7bHUGO_VERSION%7d/hugo_extended_$%7bHUGO_VERSION%7d_linux-amd64.deb) \
    && sudo dpkg -i ${{ runner.temp }}/hugo.deb
- name: Install Dart Sass Embedded
run: sudo snap install dart-sass-embedded
- name: Checkout
uses: actions/checkout@v3
with:
submodules: recursive
fetch-depth: 0
- name: Setup Pages
id: pages
uses: actions/configure-pages@v3
- name: Install Node.js dependencies
run: "[[ -f package-lock.json || -f npm-shrinkwrap.json ]] && npm ci || true"
- name: Build with Hugo
env:
# for maximum backward compatibility with hugo modules
HUGO_ENVIRONMENT: production
HUGO_ENV: production
run: |
    hugo \
    --gc \
    --minify \
    --baseURL "${{ steps.pages.outputs.base_url }}/"
- name: Upload artifact
uses: actions/upload-pages-artifact@v1
with:
path: ./public

# deployment job
deploy:
environment:
name: github-pages
url: ${{ steps.deployment.outputs.page_url }}
runs-on: ubuntu-latest
needs: build
steps:
- name: Deploy to GitHub Pages
id: deployment
uses: actions/deploy-pages@v1
```
5.  Commit and push
6.  GitHub > **Actions**. Check that workflow ran.
