---
layout: post
Title: Problems with Jekyll, Github pages on Linux Mint 17.1
cetegory: Technology
---



This site is ran using Jekyll and is hosted on Github pages. I used [this](https://help.github.com/articles/using-jekyll-with-pages/) guide to help me setup Jekyll.  I wanted to be able to host the site locally and see what the changes look like before i publish them.  That guide is pretty straight forward but here are a few problems i ran into:

### Installing Jekyll

On the github pages that explains how to install Jekyll, step 3 says to create the Gemfile and run `bundle install` and you're good to go; not the case in Linux Mint 17. It seems there is a problem with nokogiri.  The problem is it's missing some dependencies and when you try to install nokogiri via bundle it tries to install it's own version of the depencies, but fails for some reason.  I fixed it by installing these packages:

```
$ sudo apt-get install libxslt-dev libxml2-dev
```

Once those are installed you want to tell bundle to use the system libraries by running:

```
bundle config build.nokogiri --use-system-libraries
```

Then you can run `bundle install` again and it'll install Jekyll.

### Node.js

another thing that github forgets to explain is that before you can run `bundle exec jekyll serve` you have to install node.js or bundle will complain that it could not find a JavaScript runtime. To install Node.js, run:

```
$ sudo apt-get intall node.js
```

Then run `bundle exec jekyll serve` and you can access your site at 'http://localhost:4000'.



