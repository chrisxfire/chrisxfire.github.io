---
layout: post
title: "notes: adding comment functionality to a jekyll-powered blog"
date: 2023-01-18
categories: notes jekyll github-pages giscus
---
<style>
r { color: Red }
o { color: Orange }
g { color: Green }
b { color: Blue }
</style>
###### abstract
These are notes on how to add comments functionality to your Jekyll-powered blog using [giscus][giscus-site].

# background
Giscus uses GitHub Discussions to power the comments functionality for your site.  Giscus is inspired by [utterances][utterances-site] which is similar except that it uses GitHub Issues instead of Discussions.

# configure github repo
In your GitHub repo:
1. Navigate to **Settings** > **General** > **Features** section > Enable **Discussions**.
1. Navigate to the **Discussions** tab: > Click the pencil icon
[!gh-discussions-categories-pencil]({{ site.baseurl }}/assets/images/gh-discussions-categories-pencil.png)
1. Click **New Category** > **Title="Discussions"** > optional: add a **Description**> Under **Discussion Format** select **Announcement** > **Create**
1. Optional: Delete any Discussion categories you don't want

Your categories should now look similar to this:
[!gh-discussions-categories]({{ site.baseurl }}/assets/images/gh-discussions-categories.png)

[giscus-site]: https://giscus.app/
[utterances-site]: https://github.com/utterance/utterances

# install giscus
Install Giscus on your site.
Navigate to [giscus][giscus-site] and follow the well-designed instructions there:
1. When selecting <g>Page <--> Discussions Mapping</g>, select **pathname**
1. Uncheck **Use strict title matching**
1. Under **Discussion Category**, select the **Discussions** category you created above
1. Check **Only search for discussions in this category**
1. Optional: Check **Place the comment box above the comments**
1. Check **Load the comments lazily** for better site performance
1. Copy the `<script>` the site provides.

# configure jekyll
Rather than having to copy that script to each post, you can override Jekyll's default post template and add the script there.  The default post template is stored by your theme (I use `minima`).
1. Find your theme's path.  From a terminal run **bundle info --path *theme***
1. Navigate to that path + `/_layouts/post.html`
1. Edit `post.html` and paste the `<script>` at the bottom of the file.
1. Copy `post.html` to your site's directory + `/_layouts/post.html` (create `/layouts` if you don't already have it)

Jekyll will now use this version of `post.html` as the template for each of your blog posts.

# test
Create a new blog post and confirm that comments show at the bottom of the page.
[!gh-discussions-comments]({{ site.baseurl }}/assets/images/gh-discussions-comments.png)