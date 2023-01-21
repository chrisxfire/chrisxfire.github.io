---
layout: post
title: "a walk through the minefields (how this blog was built)"
date: 
categories: jekyll github-pages ruby
---
<style>
r { color: Red }
o { color: Orange }
g { color: Green }
b { color: Blue }
</style>
###### abstract
This is a guide on how to build a blog with GitHub Pages + Ruby + Jekyll along with lessons the author learned
along the way so as to make life easier for those who endeavor on this journey in the future.

# a walk through the minefields
Once upon a time (*a week before Christmas 2022*), the bug to build a blog bit.  Using a [static site generator][static-site-gen]
would keep things simple and, after some quick research, I settled on [Jekyll][jekyll].  Since Jekyll has built-in support for 
[GitHub Pages][github-pages], hosting is solved for as well.  This stack (GitHub Pages + [Ruby][ruby] + Jekyll) is all new to 
me, which is part of the draw.

The [GitHub Pages docs][github-pages-docs] indicate the process is well-baked and painless.  As you can imagine, though, 
reality does not always match the documentation.  There are landmines along this path.  What follows is the process to build 
a blog with GitHub Pages + Jekyll along with markers for those landmines :boom:.

This guide makes a few assumptions:
1. You are familiar with the basics of repositories using Git and GitHub
1. You are using Windows 10 or 11
1. You are creating a a personal blog site (not an organizational blog site)

## building the blog
### installing pre-requisites
1. Use [RubyInstaller][rubyinstaller-org][^warning] to install Ruby and an execution environment (DevKit).
1. From the [terminal][windows-terminal] (you are using terminal, yeah?), run `ridk install` ([r]uby [i]nstaller [d]evelopment 
[k]it) if it does not launch automatically after step 1.
1. Select option **3**.
1. Run `ridk enable`.
1. Run `ridk version` to confirm everything installed correctly.

### setting up github pages
1. On GitHub, create a new repository named *username*.github.io.  Some rules here:
    * You (not an organization) MUST be the owner (duh?).
    * *username* MUST match your GitHub username exactly.
    * If your GitHub username has any uppercase characters, change them to lowercase.
    * The repo visibility MUST be **public**.
    * **Initialize the repo with a README**.
2. Navigate to your newly-created repo > **Settings** > **Pages**
    * Now, choose a [publishing source][github-pages-publishing-source].  There are two options:  
        a. **Deploy from a branch**
        b. **GitHub Actions**.

Let's look at those options closely:
A. **Deploy from a branch**�changes to the branch you specify result in a baked in GitHub Actions workflow being triggered.  
    * The source branch can be any branch, but the source folder must be either `/` or `/docs`.  If you choose `/docs` and later move your content to `/`, this will break.
    * :boom: <r>You cannot change the baked in GitHub Actions workflow</r>.
    * :boom: <r>You are locked into the versions of Jekyll, minima, and other gems [specified here][github-pages-dependencies]</r>.
    At the time of this writing:  
        * Jekyll v3.9.2 is locked in, v4.3.1 is available.
        * Minima v2.5.1 is locked in, v3+ is available is which is required to allow for the dark skin that this site uses.
    * Because of these restrictions, I ended up going with option b:
B. **GitHub Actions**�with this option, you create [a custom GitHub Actions workflow][github-pages-custom-github-actions-workflow] to deploy your site.
    * You are not limited to a specific version of Jekyll or any other gems.

### installing jekyll and bundler
Here's a couple of Ruby concepts to know for this next section:
* *gem*�code that can be included in Ruby projects (much like packages or modules in other programming languages)
* *gemfile*�a list of Gems used by a Jekyll site.  Every Jekyll site has a Gemfile in its main folder.
* *bundler*�a Gem that installs all other Gems listed in the Gemfile.

To install Bundler and Jekyll:  `gem install bundler jekyll`

### create a new jekyll site
1. Clone your repo.
1. If deploying from a branch, switch to it and the source directory.
1. Create the Jekyll site:  `jekyll new --skip-bundle .`

### configure the site
1. Edit your `Gemfile`.  
    * If you went with the GitHub Actions publishing source, you can include `gem "jekyll", "~> 4.3.1"` at the top of the file 
    to use Jekyll v4.3.1 (or whatever version you like).
    * Include `gem "minima", github: "jekyll/minima"` to use Minima v3+ instead of v2.5.1.
1. Edit `_config.yml`.  Minima v3+ lets you do neat things like setting a custom date format, using the dark skin, including links
to social platforms, and setting author information.  See the `_config.yml` in this repo for an example.
1. Run `bundle install`.
1. `git add .` > `commit` > `push`. 


[github-actions-starter-workflow-jekyll]: https://github.com/actions/starter-workflows/blob/main/pages/jekyll.yml
[github-actions-starter-workflows-jekyll-gh-pages]: https://github.com/actions/starter-workflows/blob/main/pages/jekyll-gh-pages.yml
[github-pages]: https://pages.github.com/
[github-pages-custom-github-actions-workflow]: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site#creating-a-custom-github-actions-workflow-to-publish-your-site
[github-pages-dependencies]: https://pages.github.com/versions/
[github-pages-docs]: https://docs.github.com/en/pages
[github-pages-publishing-source]: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site
[jekyll]: https://jekyllrb.com
[ruby]: https://www.ruby-lang.org/en/
[rubyinstaller-org]: https://rubyinstaller.org
[rubyinstaller-warning]: https://rubyinstaller.org/about/comparison/
[static-site-gen]: https://en.wikipedia.org/wiki/Static_site_generator
[windows-terminal]: https://github.com/microsoft/terminal

[^warning]: There is an ominous warning over at [rubyinstaller.org][rubyinstaller-warning]: 
"*Although the Ruby community is continuously working to make the experience of using Ruby on Windows as 
smooth as possible, it's still slower and less convenient compared to Linux or MacOS. Some of the 
shortcomings are due to certain Windows operating system internals (such as its poor shell support), and 
others are due to the fact that so many Ruby developers simply prefer a UNIX-style system.*" This is 
categorical horseshit, but perhaps we'll save that for another post.  Suffice it to say that this page 
should serve as the warning sign on the fence of the minefield.