---
layout: post
title:  personal website on github
date: 2023-03-06 21:01:00
description: a quick tutorial on setting up your personal website on github.
categories: github jekyll
---

Are you ready to create your own personal website but are feeling overwhelmed by the process? Don't worry, you're not alone! I've been in the same boat, wanting to build my own website for ages, but always putting it off because I thought the process of creating something I truly loved would be too time-consuming.

But recently, I stumbled upon some academic webpages hosted on GitHub that caught my eye. To my surprise, I learned that many of these websites were built using templates as a starting point, making the process of building a website much simpler than I had previously thought.

Feeling inspired, I decided to take the plunge and create my own site. And guess what? I found the process to be quite straightforward and pretty enjoyable! So if you're interested in creating your own website but aren't sure where to start, keep reading. In this blog post, I'll share the different steps I followed to get my website up and running. Who knows? Maybe it will inspire you to do the same!

## My setup
I used a MacBook Pro laptop running macOS 13.1 for this project. However, the steps described in this post should also work on other operating systems, as [Jekyll](https://jekyllrb.com/) is designed to be platform-agnostic. Keep in mind that some commands and tools may have different syntax or require different installation procedures depending on your system, so you may need to adapt the instructions accordingly.

## 0 Prerequisites

Before you start building your website, it's important to ensure that you have a [GitHub](https://github.com/) account. If you don't have one, you can create a new account and log in to get started. Additionally, we will need support from [Jekyll](https://jekyllrb.com/), a static site generator that's great for creating blogs and personal websites. 

To make sure that Jekyll is properly installed in your system, you can run: 

{% highlight bash %}
jekyll -v
{% endhighlight %}

If missing, read the next section and follow the instructions for installation (or see visit [Jekyll](https://jekyllrb.com/) site).

With these two tools, you'll be well-equipped to start building your website!

### Install Jekyll
[Jekyll](https://jekyllrb.com/) is a static site generator that takes text written in a markup language and uses layouts to create a static website. To use it, you'll need to ensure that your system has a few dependencies installed:

* Ruby version 2.5.0 or higher
* RubyGems
* GCC and Make

To check if Ruby and RubyGems are already installed on your system, you can run two simple commands:

{% highlight bash %}
ruby -v
gem -v
{% endhighlight %}

If you receive output that indicates the versions of Ruby and RubyGems, you're good to go! We can install jekyll by running:

{% highlight bash %}
gem install jekyll bundler
{% endhighlight %}

If not, you'll need to install them (see section below) before you can use [Jekyll](https://jekyllrb.com/).

### Install Ruby

[Ruby](https://www.ruby-lang.org/en/) is a popular open-source programming language known for its dynamic and flexible nature. If you're interested in using Ruby, you'll need to install it on your system. Fortunately, there are several tools available to simplify the installation process, such as [Homebrew](https://brew.sh/) and [chruby](https://github.com/postmodern/chruby).

If you're a macOS user, it's worth noting that while Ruby comes preinstalled on your machine, it's recommended to install a separate and newer version using a version manager like [chruby](https://github.com/postmodern/chruby) or [rvm](https://rvm.io/). This will ensure that you have access to the latest features and security updates. For my own installation process, I followed the [jekyll](https://jekyllrb.com/docs/installation/macos/) guide and used [chruby](https://github.com/postmodern/chruby).

To check if [Ruby](https://www.ruby-lang.org/en/) is already installed on your system, you can run the `ruby -v` command in your terminal. If you see a version number displayed, you're good to go. Otherwise, you'll need to install [Ruby](https://www.ruby-lang.org/en/) before you can proceed with using it.

#### Install Homebrew

The first step to installing Ruby on your macOS or Linux system is to install [Homebrew](https://brew.sh/), a package manager that makes it easy to install software that isn't included with your operating system. [Homebrew](https://brew.sh/) allows you to easily install, upgrade, and manage packages and dependencies on your system. To install Homebrew, you can run this simple command:

{% highlight bash %}
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
{% endhighlight %}

#### Install chruby and ruby-install

To install `chruby` and `ruby-install`, we can simply run the following command in our terminal:

{% highlight bash %}
brew install chruby ruby-install xz
{% endhighlight %}

#### Install Ruby

Once installed, we can use `ruby-install` to download and install the specific version of [Ruby](https://www.ruby-lang.org/en/) that we need.

For example, to install the latest stable version of [Ruby](https://www.ruby-lang.org/en/) supported by Jekyll, we can run:

{% highlight bash %}
ruby-install ruby 3.1.3
{% endhighlight %}

This will take few minutes.

#### Configuration

After installation, we can switch to the newly installed Ruby version using `chruby`. However, before doing that, you'll need to configure your shell to automatically use `chruby`. This is typically done by adding a few lines of code to your shell configuration file, such as `.bashrc` or `.zshrc`. For example, I ran these commands:

{% highlight bash %}
echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.zshrc
echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.zshrc
{% endhighlight %}

Finally, we could add a further line to switch to our newly installed version:

{% highlight bash %}
echo "chruby ruby-3.1.3" >> ~/.zshrc 
{% endhighlight %}

And that's it! Now we have Ruby installed and ready to use on our system.

## 1 Get your template

To start, we need to choose a Jekyll theme that will serve as a foundation for our website. Fortunately, there are many free options available online, which can be easily accessed through platforms like [GitHub](https://github.com/search?q=jekyll+theme). For this tutorial, we will be using the [al-folio](https://github.com/alshedivat/al-folio) theme, which is a simple and elegant option for academics.

Once you have chosen your preferred theme, the next step is to fork the repository. To do this, simply click on the `Use this template` button and select `Create a new repository` from the dropdown menu. This will create a new repository on your GitHub profile that contains all the files from the original theme repository.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/create_new_repo.png" title="create new repo" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Make sure to rename the repository to `YOURUSERNAME.github.io` so that it can be properly published as a GitHub Pages site.

## 2 Clone your repository

Now that we have our repository set up on GitHub, we'll want to clone it to our local machine so we can start customizing it.

First, click on the `Code` button on the repository page and copy the URL provided.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/clone_repo_edit.png" title="clone a repo" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

Next, open up your terminal and navigate to the directory where you want to store your project. Once you're in the right directory, run the command:

{% highlight bash %}
git clone YOUR_REPOSITORY_URL
{% endhighlight %}

where `YOUR_REPOSITORY_URL` is the URL you copied earlier. This will download all of the code from your GitHub repository onto your local machine, allowing you to make changes to the site configuration and content.

## 3 Modify the code

Now that we have the code on our local machine, we can start modifying it. Here are some files you might want to check if you decided to use my same theme:

* `_config.yml`: this is a configuration file schema, and contains several information that will be used for the creation of the website
* `_news`: folder containing news announcements as markdown files
* `_pages/about.md`: markdown file that should contain your personal information
* `_pages/cv.md`: markdown file used to provide CV information together with `_data/cv.yml`
* `_pages/dropdown.md`: markdown file for defining submenus
* `_pages/projects.md`: markdown file used to render information on projects you are working on. It takes the information from the markdown files contained in the `_projects` folder
* `_pages/publications.md`: markdown file used to render the publications provided in `_bibliography/papers.bib`
* `_pages/repositories.md`: markdown file used to render information on the repositories provided in `_data/repositories.yml`
* `_pages/teaching.md`: markdown file that should contain your teaching experience
* `_posts`: folder containing blog entries as markdown files
* `_sass`: folder containing Sassy Cascading Style Sheets for the website
* `assets/img`: folder containing images
* `assets/pdf`: folder containing pdf files

Since sometimes there are execution issues, you might also want to add this lines to `.github/workflows/deploy.yml`:

{% highlight yml linenos mark_lines="5 6 7" %}
jobs:
    deploy:
        runs-on: ubuntu-latest
        steps:
        - name: Fix permission
            run: |
                chmod a+x bin/*
{% endhighlight %}

## 4 Build it locally

We can now build our website and make it available on a local server by running the following command:

{% highlight bash %}
bundle exec jekyll serve
{% endhighlight %}

This allows us to check if everything is as we expected, or if we need further refinement. After running the command, we can go to `http://localhost:4000/` on our web browser to see the website locally.

## 5 Upload on GitHub

Finally, we can deploy our website on GitHub. For doing so, the preferred way is by executing the following command:

{% highlight bash %}
bin/deploy --user
{% endhighlight %}

If the GitHub Actions are properly setup, your personal website should be built and available in few minutes!