---
title: Jekill Website on Github
crawlertitle: Jekill website on github
summary: Jekyll + github = Your website
date: 2019-04-27T04:00:00.000+00:00
categories: posts
tags: guides_and_tutorials
author: Lemys Lopez
lang-ref: jekyll-on-github-website
bg: "/jekyll_on_github.png"

---
Github is well know as the "biggest database of software code" but nowadays their public non paid services, allows you to  serve static web files to as your own website (just like this one that you are reading). This lines will guide you through  the process of publishing some static web-files, generated with the use of a popular ruby coded tool called Jekyll, on github pages using the linux terminal.

In this guide **I’ll assume you have some basic knowledge about how a website works, some experience using git with a github account,** and also that you are using a current stable version of Debian or some debian based os like Ubuntu, i will focus only in the process of creating a new site with jekyll locally and then pushing it on github.

\### Installing dependencies

Jekyll was developed with ruby, and therefore it makes planty use of some of it gems, also some development tools libraries and header files are needed, they are shipped to us inside build-essential and zlib1-dev deb packages. You can install them using apt (or your favourite package manager), running a command like this might be enough to get them:

    sudo apt-get install ruby-full build-essential zlib1g-dev git

\### Configuring gems with a user directory

It's not a good thing to install ruby gems as a root user, thats why to create a gems dir, that holds all of our libs, is a better approach, so thats the first thing to do to create a gems dir:

    $ cd ~ \ 
    $ mkdir gems

So we need to edit our  \~/.bashrc file, adding a new environment var (**GEM_HOME**), and updating the value of another (**PATH**),  you can edit the file with you fav text editor, i like to use nano: 

    $ nano .bashrc

	

Then at the very end type something like this:

    #gem stuf 
    export GEM_HOME="$HOME/gems" 
    export PATH="$HOME/gems/bin:$PATH"

Finally we load the file and we are ready to install some gems stuff:

    $ source ~/.bashrc

\### Installing Jekyll and github-pages

\**	**Now with properly setted ruby environment we can continue installing jekyll and other ruby tools like bundler and github-pages the last one is like a metapackage with all ruby gems for a github based jekyll website:

    $ gem install jekyll bundler git  github-pages

	So far if nothing goes wrong we are ready to create a new jekyll site.

\### Creating a new jekyll site

	It can be done using the jekyll command where user its your own username at github.com:

    $ jekyll new user.github.io 

	Remember to replace “user” with your github username, then we change to our newly directory containing the files of our site:

    $ cd user.github.io

	It should have a directory tree  like this: 

    $ tree
    ├── 404.html
    ├── about.md
    ├── _config.yml
    ├── Gemfile
    ├── index.md
    └── _posts
    	└── 2019-04-29-welcome-to-jekyll.markdown

\### Editing the Gemfile for github, update gems and test

	It necessary to comment the line that use the jekyll version and uncomment the one that install the gem github-pages to do so just prepend a # at the beginning of the line number 11, and remove the # from the line number 18, the gemfile should look similar to this 

{% highlight bash %} 

10 # Happy Jekylling!

11 gem "jekyll", "\~> 3.8.5"

12

13 # This is the default theme for new Jekyll sites. You may change this to anything you lik$

14 gem "minima", "\~> 2.0"

15

16 # If you want to use GitHub Pages, remove the "gem "jekyll"" above and

17 # uncomment the line below. To upgrade, run \`bundle update github-pages\`.

18 # gem "github-pages", group: :jekyll_plugins

{% endhighlight %}

	Then you can update the gems with the bundle command:

$ bundle update

	Jekyll comes with a web server for local testing, and bundle tool checks for changes in the code to fire things up just run:

$ bundle exec jekyll serve --host=0.0.0.0

	Now if you open your favourite browser at localhost:4000 you should be able to view your site.

\### Push your site to github

	First you need to create a repository project on github.com with you github username prepend to github.io, in shot a new project repository with the same name of your newly directory containing the files of your site (user.github.io), then initialize git tracking and configure where to push with the following commands: 

$ git init

$ git remote add origin git@github.com:user/user.github.io

$ git push -u origin master

	Finally you will be able to view your site at http://user.github.io.