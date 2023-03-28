---
title: "Create GitHub Pages Using Hugo"
date: 2023-03-16T15:44:40+03:30
type: "post"
tags: ["GitHub", "Hugo"]
---
Github provides this excellent feature where you can create your own blog/portfolio for free and Github will host your content.

The only thing you have to do is create a new repository with a specific name: **username.github.io** and replace the username with your **GitHub username**. You can upload your site or blog content to this repository.
But what if you want to have some sort of content management tool? GitHub explains how to do so using Jekyll. Jekyll is a static site generator written in Ruby. [Here](https://docs.github.com/en/pages/quickstart) is the link to the GitHub instructions for creating GitHub pages using Jekyll. Now we are going to do the same using [Hugo](https://gohugo.io/). Hugo is one of the most popular open-source static site generators with its amazing speed and flexibility written in Go. You can install it easily:

macOS

```bash
$ brew install hugo
```

Windows

```bash
$ choco install hugo-extended
```

Linux

```bash
$ sudo snap install hugo
```

Hugo has a simple, easy-to-use CLI, you can test your installation by running

```bash
hugo version
```

1. We need another repository to store our Hugo contents, our drafts, theme, etc. you can name it whatever you want.
    
    We need to clone this repository locally, after cloning we start a new Hugo site inside this directory by running:
    
    ```bash
    hugo new sit WhateverNameYouWant
    ```
    

Hugo creates a lot of boilerplate code inside that directory.

1. Now we need to select a theme for our blog. There are several free themes available for Hugo, you can find them [here](https://themes.gohugo.io/). After selecting the desired theme, we are going to clone the theme repository inside our blog/theme directory
    
    To do that, inside your blog repository, CD inside theme directory and clone the theme repository here
    
2. Set the theme as default. To utilize our theme, inside blog repository open config.toml file and set the following:
    
    ```toml
    baseURL = ''
    defaultContentLanguage = "en"
    languageCode = 'en-us'
    
    title = 'Your Blog Title'
    
    theme = "theme name"
    ```
    
3. Lets write our first post
    
    ```bash
    hugo new posts/myPostName.md
    ```
    
    This will create a Markdown file inside posts directory. You can open this file and edit your first blog post.
    
4. Now to see a preview of your blog you can simply run:
    
    ```bash
    hugo server
    ```
    
    and open the link Hugo generates.
    
5. The crucial step here is to add the repository that we want our blog content to live (the repository with your GitHub username) as a sub-module to our blog repository.
    
    ```bash
    git submodule add -b main repoURL public
    ```
    
    The reason why we call our destination folder public is that when Hugo renders our content it will store the results in a folder named public, by doing so we don’t need to copy rendered content to where our GitHub pages repository gonna live.
    
6. To generate the static files we just run:
    
    ```bash
    hugo -t themeName
    ```
    
    The generated files go to the public directory.
    
7. Inside the public directory if we check the remote origin points to our GitHub page repository (username.github.io), so the only thing that is left is to commit static content to this repository.

Now you can go to http://username.github.io and enjoy your blog. 

There would be also some configuration regarding the theme you have selected, for instance how the home page should look like, which is usually explained in theme repository.

Here are some useful resources:

[Creating a Blog with Hugo and Github in 10 minutes](https://www.youtube.com/watch?v=LIFvgrRxdt4)
