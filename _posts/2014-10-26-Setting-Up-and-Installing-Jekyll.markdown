---
layout: post
title: "Setting Up and Installing Jekyll"
categories: jekyll blog
tags: jekyll blog
---
[Jekyll][jekyll] is a site generator (*built with [Ruby](https://www.ruby-lang.org/en/)*) for building highly customizable blogs.  [Jekyll][jekyll] is also the core engine behind [GitHub Pages][GitHub Pages], which allows users to host static sites directly from your [GitHub](https://github.com/) repository.  If you have ever used CMS or blogging giants like [wordpress](https://wordpress.com/), and experienced performance or troubleshooting issues, [Jekyll][jekyll] may be a welcome change of pace.  For those wanting a quick 'plug and play' platform, you may find [Jekyll][jekyll] a little intimidating at first.  However, once you understand the basic file structure and workflow, you will likely be more than impressed at its' ease of use.

To really get the most out of [Jekyll][jekyll], you should have (*but not required*) a basic understanding of:

- [HTML](http://www.w3schools.com/html/)
- [CSS](http://www.w3schools.com/css/)
- [Markdown](http://daringfireball.net/projects/markdown/)
- [Git](http://git-scm.com/)

This post **is not** a complete guide on how to create a blog with [Jekyll][jekyll], but rather a guide to installing and hosting a blog using [Jekyll][jekyll] on [GitHub][GitHub Pages].  The documentation on [Jekyll][jekyll] is very comprehensive, and should be used to guide you into building a solid blog. 

### Installation
I am using a Mac OSX environment, and although Windows is not officially supported, you can get Windows specific docs [here](http://jekyllrb.com/docs/windows/#installation).  Before installing Jekyll, you will need to already have [Ruby](https://www.ruby-lang.org/en/downloads/), [RubyGems](http://rubygems.org/pages/download), and [NodeJS](http://nodejs.org/).  You can check if you already have these installed by using Terminal command line:

{% highlight text %}
node -v
ruby -v
{% endhighlight %}

If you have [Homebrew](http://brew.sh/), a package manager for OSX, you can install them easily by typing:

{% highlight text %}
brew install ruby
brew install node
{% endhighlight %}

Once you have installed all of the pre-requirements, installing [Jekyll][jekyll] should be straightfoward using the command:

{% highlight text %}
sudo gem install jekyll
{% endhighlight %}

You can create your new site wherever you like, but I like to organize it in **Documents/blog**.  Here I can create multiple blogs and have them in one central location.  The blog does not need to be saved in you **sites** folder, because you will serve your site locally with its' own server.  To create your site files, use the following commands (*change my-new-blog to your blog's name*):

{% highlight text %}
mkdir ~/Documents/blog && cd ~/Documents/blog
jekyll new my-new-blog
cd my-new-blog
{% endhighlight %}

You should now see a [Directory Structure](http://jekyllrb.com/docs/structure/) that looks like the one below:

{% highlight text %}
├── _config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _data
|   └── members.yml
├── _site
└── index.html
{% endhighlight %}

### Serving Your Site Locally
You can now use [Jekyll][jekyll]'s command line interface to [build and serve](http://jekyllrb.com/docs/usage/) your changes and generate the static HTML of your site.  When you use **build**, your are generating your site.  Using **serve** generates your site, and launches a built-in web server to preview your site locally in your browser.  To do this, you will need to type the following:

{% highlight text %}
jekyll serve
{% endhighlight %}

Once the local web server is deployed, you can go to [http://localhost:4000](http://localhost:4000) to view your site.  The site uses a default template provided by [Jekyll](jekyll).  You will need to read through their documentation to learn how to create modify your site and create new entries.

### Deploying to GitHub Pages
With [GitHub Pages][GitHub Pages], you can create one user site and unlimited project sites.  For this example, we are going to create a project site to push our blog to.  If you do not already have an existing [GitHub](https://github.com/) account, you will need to create one.

[jekyll]: http://jekyllrb.com
[GitHub Pages]: https://pages.github.com/
