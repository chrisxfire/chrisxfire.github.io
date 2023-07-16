---
title: notes > code > web > github pages > overview
date: 2022-12-21T00:00:00-07:00
draft: false
weight: -1
---

# Overview
Use GitHub Pages to host a website about yourself, an organization, or a project directly from GitHub.com.

# How it Works
GitHub Pages takes HTML, CSS, and JS files from a repo, optionally runs them through a build process, and publishes a website.  
Sites can be hosted on `github.io` or a custom domain.

Types
- User:  `username.github.io`
- Org:  `organization.github.io`
- Project:  `username.github.io/repository`

# Publishing Sources
A GHP site can publish when changes are pushed to a specific branch by configuring a publishing source.  The publishing source is a branch and a folder:
- The branch can be any branch
- The folder can be either `/` or `/docs` on that branch

Publish a site from a source branch to use Jekyll as the static site generator.

# Static Site Generators
To use something other than Jekyll, place an empty `.nojekyll` file in root of publishing source.
No support for PHP, Ruby or Python.

# Publishing a GitHub Pages Site
- New repo > *username.github.io* > Check **Initialize with README** > **Create**
- Navigate to new repo > create an entry file
		○ GitHub Pages looks for `index.html`, `index.md`, or `README.md` as the entry file.

# Creating a Publishing Source
Navigate to repo > **Settings** > *Code and automation* > **Pages** > *Build and deployment* > *Source* > **Deploy from a branch** > *Branch* > **None** or select a publishing source > select a folder > **Save**

If the publishing source `/docs` on main branch, entry file must be in `/docs` folder on main.

Additional files follow the same directory structure as the publishing source:  a new file called `/about/contact-us.md` on `main` will be available at `https://username.github.io/repository/about/contact-us.html`

# Creating a Custom 404 Page
1. Navigate to repo > navigate to publishing source > Add file > Create new file > 404.html or 404.md 
2. Add this front matter:
    ```
    ---
    permalink: /404.html
    ---
    ```
3. Below the front matter, add any content you want.
4. Commit
	
U# npublishing a GitHub Pages Site
Navigate to repo > **GitHub Pages** > **…** > **Unpublish site**

# Custom Domain
Use an apex domain and `www` subdomain.

## Configuring an Apex Domain
1. Navigate to repo > **Settings** > *Code and automation* > **Pages** > *Custom domain* > enter the custom domain > **Save**
2. If publishing from a branch, this creates a commit with a CNAME file to root of the source branch.
3. DNS provider > create A records that points the apex domain to these IP addresses:
    ```
    185.199.108.153  
    185.199.109.153  
    185.199.110.153  
    185.199.111.153  
    ```
1. For AAAA records:
    ```
    2606:50c0:8000::153
    2606:50c0:8001::153
    2606:50c0:8002::153
    2606:50c0:8003::153
    ```

Then, configure Subdomain
1. DNS provider > create a CNAME record that points subdomain to `username.github.io`

## Verify a Domain
1. Profile photo > **Settings** > **Code, planning, and automation** > *Pages* > Add a domain > enter domain name
2. Follow instructions under *Add a DNS TXT record*
3. Wait for DNS changes to propagate
4. Profile photo > **Settings** > **Code, planning, and automation** > *Pages* > **…** > Continue verifying > **Verify**
