# My blog

## Notes to self

### Create new post

> Based on [the official Posts guide](https://jekyllrb.com/docs/posts/)

Add a file to the `_posts` folder on the format `YEAR-DAY-MONTH-TITLE.md`.

All posts must start with front matter (meta data inside a block of three dashes). Use this template:

```text
---
layout: post
title:  "TITLE"
date:   YYYY-DD-MM HH:MM:SS +0100
categories: [category]
tags: [tag]
permalink: /LINK/
---
```

Add as many tags as you want to describe the post. Add few categories (because they can be part of the url). Categories is meant to group posts in a hierarchy (is my understanding).

### Install

1. Ruby
2. Bundler with `gem install bundler`
3. Everything else in the Gemfile with `bundle install`

### Run locally

Run with `bundle exec jekyll serve`
