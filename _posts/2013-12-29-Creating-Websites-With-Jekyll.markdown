---
layout: post
title: "Creating Websites With Jekyll"
date: 2013-12-29 14:43:00:00
categories: jekyll update
---

In an effort to create an on-line presence where I could share things about my professional experiences and endeavors I decided to create a website.  An additional benefit was that I could also begin experimenting with web development.    Through my normal web browsing I noticed that many personal websites were built with Jekyll so I decided to take a closer look.  That brings me to this post.

## What is Jekyll?
	
Jekyll is a static site generator.  Given a collection of files written in markdown (Markdown or Textitle) or HTML, Jekyll acts as a transformation engine producing a static web site.  All this is done locally on your desktop, no database or administration so you don't have to worry about loss of data, constant updates, or security flaws.  Yet, there is enough flexibility to custom design your website with any HTML or CSS design you like.  Use your favorite text editor and version control system such as GitHub to push any site changes.  Tom Preston-Werner co-founder of GitHub developed Jekyll and in fact GitHub is built with Jekyll.  As an added bonus GitHub offers free hosting for your website via GitHub Pages.  

Jekyll is written in Ruby so you need to start off by installing Ruby and Ruby Gems, then install Jekyll.  It is best to use a linux operating system as Jekyll is not supported for Windows.  I believe it is possible to run in a Windows environment, but I haven't explored this option.  Ruby may be already installed on your linux environment, type the following to check your version number: 

{% highlight linux-config %}
$ ruby -v 
{% endhighlight %}

If it is not installed you can follow directions <a href="https://rvm.io/" "target=_blank">here</a>.  Ruby gems can be installed by following the directions <a href="https://rubygems.org/pages/download" "target=_blank">here</a>.  Once gems is installed type: 

{% highlight linux-config %}
$  gem install jekyll
{% endhighlight %}

If you plan on using markdown instead of HTML to create your blog posts install Rdiscount.

{% highlight linux-config %}
$ sudo gem install rdiscount
{% endhighlight %}

Another useful install if you want to add code syntax in your blog posts is Pygments.  Pygments is written in Python and requires an installation to run Pygments.

{% highlight linux-config %}
$ sudo easy_install Pygments
{% endhighlight %}

That concludes the set up necessary for Jekyll.  You  can generate a simple site created by Jekyll and view it at http://localhost:4000 by typing:

{% highlight linux-config %}
$ jekyll new myblog
$ cd myblog
$ jekyll serve
{% endhighlight %}

Goto the link above and you have a working site. 

## Jekyll Configuration

So now you are going to want to configure Jekyll to create your own site.  Let's take a look at what happened when we executed jekyll new my blog.  If you take a look inside the directory you will see it generated some directories and two files:  

{% highlight linux-config %}
_includes
_layouts
_posts
_site
_config.yml
index.html
{% endhighlight %}

Jekyll expects the above directory structure to generate your website.  I'll give a brief description of the different files. 
 _config.yml contains configuration information where you can add different variables to customize your site.  
_includes directory contains sections of html such as head, footer, and navigation html which you can inject into other pages via liquid tags.  It facilitates code reuse to help organize your files. 
_layouts directory contain html files which consist of templates to define the layout of a particular page.  It is here where you can specify different sections from the _includes directory to structure pages.  For instance you may create a default layout which looks like this:

{% highlight linux-config %}
{% raw %}
	{% include header.html %}
		{{ content }}
	{% inlcude footer.html %}
{% endraw %}
{% endhighlight %}

Pages contain YAML front matter which specifies which layout to use.  For example in your index.html   file at the top of the page you must first type:

{% highlight linux-config %}
- - -
layout: default
- - - 
{% endhighlight %}

Or whatever the name of your layout your wish to use.  YAML front matter is basically configuration parameters defined at the top of pages your wish to include in your site.  If the YAML front matter is missing Jekyll will not process that particular page.

_site directory is where Jekyll stores your generated site files.  There is no need to change any files in this directory and should be left alone.  
_post directory contains your blog posts and files in this directory must be titles in the following format: YEAR-MONTH-DAY-blogtitle.markup
index.html file is the html file which is rendered first to start your site.  

At this point you will probably want to reference some html and css templates to incorporate into your site.  Find one that gives you a layout that fits what you wish to accomplish with your site and then modify it to your liking.  I found <a href="http://getbootstrap.com/">Bootstrap </a> to be particularly helpful. 

## Deployment

If you want a custom domain name to give your blog an easily remembered name then you need to register a domain name with DNS service provider which will typically charge you a monthly or yearly fee.  I opted for this route and a chose domain name registration site called <a href="http://www.1and1.com/">1and1</a>.  It was fairly easy to set up with Jekyll.  You need to add another file called CNAME and include at the top your domain name.  You also need to change the DNS settings that the provider you choose points.  This requires making the A record point to 192.30.252.153 so that it points to GitHub Pages.  GitHub Pages will finds the CNAME file with the correct domain name to publish your site.   All that is left is to push your site to GitHub and your site should be up and running.  For more information on creating a GitHub pages repository and committing files check out <a href="http://www.thinkful.com/learn/a-guide-to-using-github-pages/">this</a> webpage.  

## Conclusion

This post just covers some of the basics of Jekyll and some of the topics which I thought were most relevant.  The <a href="http://jekyllrb.com/">Jekyll</a> website and documentation does a great job of walking you through the setup and all the ins  and outs of Jekyll.  There are plenty of other writeup on how to get started with Jekyll and they all have something unique to share which may help if you run into trouble along the way.  Finally, Jekyll is a great tool for creating a custom static website or blog.  It isn't recommended for someone with no technical background, but for the technically inclined it is a great resource to quickly get a site up and running.  
  
