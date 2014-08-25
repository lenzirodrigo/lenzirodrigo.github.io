---
layout: post
title:  "Jekyll + Disqus"
date:   2014-08-24 23:10:51
comments: true
---
I've been playing with [Ruby on Rails][rails] lately and I came across to [Jekyll][jekyll], so Why not take some time and put in place a minimal site where I can share something related to technology/programming? 

Let's go:

Jekyll
------
Jekyll is a simple, blog-aware, static site generator. It takes a template directory containing raw text files, and spits out a complete static website suitable for serving with a web server. 
Having Ruby installed we can execute the following steps to create a site.  

{% highlight bash %}

~ $ gem install jekyll
~ $ jekyll new site
~ $ cd site
~/site $ jekyll serve
# => Now browse to http://localhost:4000

{% endhighlight %}

You can find more information in the [Documentation][jekyll-doc].  
Jekyll also happens to be the engine behind [GitHub Pages][GHpages], so can use Jekyll to host your project’s page, blog, or website from GitHub’s servers for free.

Github Pages
------------
[Github Pages][GHpages] is an awesome way to take advantage of a Github repository to host a page. Just edit, push, and your changes are live.

Let's move our site to Github Pages.

- Create a repository

Head over to GitHub and create a new repository named `username.github.io`, where username is your username on GitHub.

- Clone the repository

Go to the folder where you want to store your project, and clone the new repository:

{% highlight bash %}
~ $ git clone https://github.com/username/username.github.io
{% endhighlight %}

- Move the Jekyll project there
 
{% highlight bash %}
~ $ cd username.github.io
~ $ mv site/* .
{% endhighlight %}

- Push it
{% highlight bash %}

~ $ git add --all
~ $ $git commit -m "Initial commit"
~ $ $git push

{% endhighlight %}

- Done

Fire up a browser and go to `http://username.github.io`. 
Give it a couple of minutes for your page to show up—there will be a delay this very first time. In the future, changes will show up pretty much instantly.


To use a `Custom URL`, just create a file named CNAME and include your URL. Then you have to Configure a custom subdomain with your DNS provider. [Read more][GH-custom].

Disqus
------
Up to now we've set up a blog like site, which you would like to customize, and its live hosted by `Github Pages`. Now its easy to add content, I mean posts, but `Jekyll` is a static site generator, and having discussions over our posts is a must to feature.
[Disqus][disqus] is an easy way to add what we need to our site. Let's add it to the site.

- Register with Disqus

First off all [sing up][disqus-singup], during registration, you will pick a shortname for your site, which is how Disqus identifies your website community in the system.

- Install Disqus

Disqus is compatible with virtually any custom website. To Add it to our Jekyll site visit the installation instructions section, an choose the `Universal Code`.
Add the code snippet at the bottom of `_layout/post.html`, and the variable "comments: True" needs to be added in the YAML header of the post.


And that's all, feel free to take a look at my [site][lenzirodrigo] on Github or explore sites [powered by Jekyll][jekyll-powered].  


[rails]:            http://rubyonrails.org/
[jekyll]:           http://jekyllrb.com
[jekyll-doc]:       http://jekyllrb.com/docs/usage/
[jekyll-powered]:   http://jekyllrb.com/docs/sites/
[GHpages]:          https://pages.github.com/
[lenzirodrigo]:     https://github.com/lenzirodrigo/lenzirodrigo.github.io
[GH-custom]:        https://help.github.com/articles/setting-up-a-custom-domain-with-github-pages
[disqus]:           https://disqus.com
[disqus-singup]:    https://disqus.com/admin/signup/?utm_source=New-Site