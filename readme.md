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
date:   YY-DD-MM HH:MM:SS +0100
categories: [category]
permalink: /LINK/
---
```

### Install

1. Ruby
2. Bundler with `gem install bundler`
3. Everything else in the Gemfile with `bundle install`

### Run locally

Run with `bundle exec jekyll serve`
