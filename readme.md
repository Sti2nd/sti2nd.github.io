# My blog

My tech blog where I write about my experiences, lessons learned, my projects and perhaps ideas.

## Tech

My blog are currently hosted by [Github Pages](https://pages.github.com/) and use [Jekyll](https://jekyllrb.com/) to generate the site as [supported by Github Pages](https://help.github.com/en/github/working-with-github-pages/setting-up-a-github-pages-site-with-jekyll).

## Notes to self

### Create new post

> Based on [the official Posts guide](https://jekyllrb.com/docs/posts/)

Add a file to the `_posts` folder on the format `YEAR-DAY-MONTH-TITLE.md`.

All posts must start with front matter (meta data inside a block of three dashes). Use this template:

```text
---
layout: post
title:  "TITLE"
description: "DESCRIPTION"
date:   YYYY-MM-DD HH:MM:SS +0100
categories: [category]
tags: [tag]
permalink: /LINK/
lang: language_TERRITORY
image: /assets/IMAGE.png
author: "Stian Jørgensrud"
---
```

Add as many tags as you want to describe the post. Add few categories (because they can be part of the url). Categories is meant to group posts in a hierarchy (is my understanding).

Add this to the end of articles

```text
---
Last updated May 1 2020

Comments on this text? [Create an issue on Github!](https://github.com/Sti2nd/sti2nd.github.io/issues)
```

### Install

1. Ruby
2. Bundler with `gem install bundler`
3. Everything else in the Gemfile with `bundle install`

### Run locally

Run with `bundle exec jekyll serve`

Use `bundle exec jekyll serve --drafts` to see drafts as well.
