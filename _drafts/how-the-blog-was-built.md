---
layout: post
title: "a walk through the minefields (how this blog was built)"
date: 2022-12-26
categories: 
---
# a walk through the minefields
## once bitten
Once upon a time (*a week before Christmas 2022*), the bug to build a blog bit.  Using a [static site generator][static-site-gen]
would keep things simple and, after some quick research, I settled on [Jekyll][jekyll].  Since Jekyll has built-in support for 
[GitHub Pages][github-pages], hosting is solved for as well.  This stack (GitHub Pages + Ruby + Jekyll) is all new to me, which 
is part of the draw.

The [GitHub Pages docs][github-pages-docs] indicate the process is well-baked and would be relatively painless. 
Leaving it to you to define "painless," here are some things I learned along the way.

## building the blog
### installing pre-requisites
These steps assume you are running Windows 10/11:

1. Use [RubyInstaller][rubyinstaller-org][^warning] to install Ruby and an execution environment (DevKit).
1. From the [terminal][windows-terminal] (you are using terminal, yeah?), run **ridk install** (**r**uby **i**nstaller **d**evelopment **k**it) if it does not launch automatically after step 1.
1. Select option **3**.
1. Run **ridk enable**.
1. Run **ridk version** to confirm everything installed correctly.

[github-actions-starter-workflow-jekyll]: https://github.com/actions/starter-workflows/blob/main/pages/jekyll.yml
[github-actions-starter-workflows-jekyll-gh-pages]: https://github.com/actions/starter-workflows/blob/main/pages/jekyll-gh-pages.yml
[github-pages]: https://pages.github.com/
[github-pages-docs]: https://docs.github.com/en/pages
[jekyll]: https://jekyllrb.com
[ruby]: https://www.ruby-lang.org/en/
[rubyinstaller-org]: https://rubyinstaller.org
[rubyinstaller-warning]: https://rubyinstaller.org/about/comparison/
[static-site-gen]: https://en.wikipedia.org/wiki/Static_site_generator
[windows-terminal]: https://github.com/microsoft/terminal

[^warning]: There is an ominous warning over at [rubyinstaller.org][rubyinstaller-warning]: 
"*Although the Ruby community is continuously working to make the experience of using Ruby on Windows as smooth as possible, it’s 
still slower and less convenient compared to Linux or MacOS. Some of the shortcomings are due to certain Windows operating system 
internals (such as its poor shell support), and others are due to the fact that so many Ruby developers simply prefer a UNIX-style system.*"
This is categorical horseshit, but perhaps we'll save that for another post.  Suffice it to say that this page should serve as the warning
side on the fence of the minefield.