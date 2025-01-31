---
layout: post
title:  "Creating a website with GitHub Pages"
date: 2023-10-14
tags: programming
last_updated: 2024-01-28
status: final
type: note
---

A tutorial for setting up your own website using GitHub Pages.
- [Install Homebrew](#install-homebrew)
- [Install ruby](#install-ruby)
- [Install Jekyll gem](#install-jekyll-gem)


## Install Jekyll

Jekyll is a framework for generating static websites such as blogs. It is commonly used for writing blogs in markdown with GitHub pages. Jekyll is written in Ruby, we need to first install Ruby before installing Jekyll. Ruby can be easily installed with Homebrew package manager. Let's install Homebrew first! 

#### Install Homebrew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

#### Install ruby

Taken from [Jekyll documentation](https://jekyllrb.com/docs/installation/macos/) with some additional information on what and why.

1. Install `chruby` and `ruby-install`:
    ```bash
    brew install chruby ruby-install xz
    ```

    - `chruby` is a Ruby version management tool. 
    - `ruby-install` supports installing Ruby version of choice.
    - `xz` is a data compression library required by `chruby` and `ruby-install`.

2. Install the Ruby version supported by Jekyll:
    ```bash
    ruby-install ruby 3.1.3
    ```
3. Configure your shell to automatically use `chruby`:
    ```bash
    echo "source $(brew --prefix)/opt/chruby/share/chruby/chruby.sh" >> ~/.zshrc
    echo "source $(brew --prefix)/opt/chruby/share/chruby/auto.sh" >> ~/.zshrc
    echo "chruby ruby-3.1.3" >> ~/.zshrc # run 'chruby' to see actual version
    ```
    macOS defaults to `zsh` instead of `bash` since macOS Catalina. If you are using `bash`, replace `.zshrc` with `.bash_profile`. Run `echo $0` to find which shell you are using.
4. Quit and relaunch the terminal to verify we now have the correct ruby version:
  ```bash
  ruby -v
  ```
  It should output the version that starts with: `ruby 3.1.3p185`.

#### Install Jekyll gem

Now that we have installed ruby, we can install the Jekyll gem. A ruby gem is a library.

```bash
gem install jekyll bundler
```

- `bundler` is a gem that manages an application's doeendencies. We are installing it so that our demo site dependencies are automatically managed.

Aaand now we are ready to create a demo site!

## Create a GitHub repo

Follow the steps from [GitHub documentation](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site). This is the repo that will hold our site pages, posts, layout, etc.


## Create demo site

While the [official documentation](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll) for creating a demo site is great, I found [this article](https://programminghistorian.org/en/lessons/building-static-sites-with-jekyll-github-pages) more helpful.

## Run the website locally

```bash
bundle exec jekyll serve --watch
```

Website will be viewable locally at `http://127.0.0.1:4000/`.