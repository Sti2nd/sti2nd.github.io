---
layout: post
title:  "TITLE"
description: "DESCRIPTION"
date:   YYYY-MM-DD HH:MM:SS +0100
categories: [category]
tags: [tag]
permalink: /alias-online/
lang: language_TERRITORY
image: /assets/IMAGE.png
author: "Stian Jørgensrud"
---

## Mining Wikipedia for words

I read the official [download page](https://en.wikipedia.org/wiki/Wikipedia:Database_download) and first downloaded `nowiki-20210101-pages-articles.xml`. Since neither [pandas](https://pandas.pydata.org/) nor [Apache Spark](https://spark.apache.org/) can import XML out of the box, I decided to go for json format instead. After some trying and failing with converting XML (and [Wiki text](https://en.wikipedia.org/wiki/Help:Wikitext)) to JSON, I found that the [CirrusSearch option on this page](https://dumps.wikimedia.org/other/) is a json dump. So I ended up downloading `nowiki-20210111-cirrussearch-content.json.gz`, after first trying and failing with the one named `...-general.json.gz` of course...

I quickly confirmed that Python could not import the entire JSON file in memory, which was what pandas tried to do. Something beefier is [Apache Spark](https://spark.apache.org/), and I chose it simply because I had used it before.

I spent a lot of time cleaning the data. Although the dataset didn't contain wiki text, there were still some templates which made appearance as common words and phrases.

---
Last updated January 18 2021

Comments on this text? [Create an issue on Github!](https://github.com/Sti2nd/sti2nd.github.io/issues)