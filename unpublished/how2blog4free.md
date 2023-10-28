---
title: How I host this blog
date: 2022-10-15
description: ‘A quick run down on how I setup this blog, how it works and what is the cost.’
image: images/blog/blog-header.jpg
tags: [‘Blog’, ‘Hugo’, ‘Netlify’]
---

# What is free?

I pay for the domain

# What I use

## What is Hugo

Hugo is a static site generator that takes a directory with content and templates and renders them into a fully static website. Here's a more detailed breakdown of how Hugo operates to generate static websites:

1. **Content Management**:
    - Users create and manage content in the form of markdown files. These files are organized in a specific directory structure.
    - The content can include text, images, and other media.

2. **Configuration**:
    - Hugo relies on a configuration file, typically named `config.toml`, `config.yaml`, or `config.json`, to understand the structure and settings for your site.
    - In this file, you specify themes, URL structures, and other site-wide settings.

3. **Themes and Templates**:
    - Hugo uses templates to define the HTML structure of the pages.
    - Themes in Hugo encapsulate a set of templates, static files, and other assets. Users can create their own themes or use existing ones.

4. **Shortcodes**:
    - Hugo has a feature called shortcodes which allows users to create rich content without having to write HTML.
    - Shortcodes are simple snippets inside your content files calling built-in or custom templates.

5. **Static File Generation**:
    - Once the content, configuration, and templates are ready, Hugo generates the static HTML, CSS, and JavaScript files.
    - This is done via a single command `hugo`, which processes all the files and outputs them to a `public` directory by default.

6. **Preview and Development**:
    - Hugo includes a built-in web server for previewing your site during development.
    - You can run `hugo server` to start a live-reloading server that allows you to see changes in real-time as you work on your site.

7. **Deployment**:
    - After generating the static files, users can upload them to any web server or hosting platform that serves static files.
    - This makes Hugo sites fast, secure, and easy to host.

8. **Extensibility**:
    - Hugo is extensible and supports various output formats including HTML, JSON, and XML, allowing users to build APIs, and more.
    - It also supports data files, which allow you to use data from CSV, JSON, or XML files within your templates.

9. **Community and Plugins**:
    - While Hugo doesn't support plugins in the way that other systems like WordPress do, there is a community of developers who create themes and share solutions for common needs.
    - This community contributes to the robust ecosystem around Hugo, providing support and additional functionalities through themes and other shared resources.

By orchestrating the interaction between content, templates, configurations, and other features, Hugo is able to rapidly generate static websites that are easy to manage and deploy.

All pages are markdown

Site is a static site

Hugo template
Hugo generates the static site from source

Source is hosted in a free GitHub repository

Netlify is hooked up to the GitHub repository and monitors the main branch, any changes it will spin up a small container and generate a new static site.

The site is then moved to a CDN and hosted with an SSL certificate.

## The process on how I manage the blog

Git repo, vs code on the mac with the following plugins

—-screenshot—-

### On the iPad

- Working copy (free)
- iCloud Drive (Working Copy adds your synced GitHub repository in files)
- Markdown editor of choice (i use either working copy and if I need pretty you have a free preview in working copy)
- Keep all new posts, edits and changes on an unpublished branch.
- Once you are happy, merge to your main branch and Netlify will build site and update your CDN

### Stuff to research

- how does Hugo work
- how does Netlify work
- where does it host the stuff
- how does the SSL cert work…

URL - <https://gohugo.io/hosting-and-deployment/hosting-on-netlify/>
