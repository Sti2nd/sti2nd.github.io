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

To create a word game we need some words. Wikipedia have a list of the most frequently used words [on this link](https://en.wiktionary.org/wiki/Wiktionary:Frequency_lists/Norwegian), but I didn't know that, and where is the fun! This require some serious over-engineering!

## Mining Wikipedia for words

I read the official [download page](https://en.wikipedia.org/wiki/Wikipedia:Database_download) and first downloaded `nowiki-20210101-pages-articles.xml`. Since neither [pandas](https://pandas.pydata.org/) nor [Apache Spark](https://spark.apache.org/) can import XML out of the box, I decided to go for json format instead. After some trying and failing with converting XML (and [Wiki text](https://en.wikipedia.org/wiki/Help:Wikitext)) to JSON, I found that the [CirrusSearch option on this page](https://dumps.wikimedia.org/other/) is a json dump. So I ended up downloading `nowiki-20210111-cirrussearch-content.json.gz`, after first trying and failing with the one named `...-general.json.gz` of course...

I quickly confirmed that Python could not import the entire JSON file in memory, which was what pandas tried to do. Something beefier is [Apache Spark](https://spark.apache.org/), and I chose it simply because I had used it before. It is supposed to be a tool one can use on your standard off-the-shelves computers for Big Data. Since it is meant for large data, it means it will store data on the disk instead of in memory. And it of course supports parallelism. Although the real power comes from the ability to run in a cluster, I will just use my own single computer.

I spent a lot of time cleaning the data. Although the dataset didn't contain wiki text, there were still some templates which made appearance as common words and phrases. These templates I gave up removing. I decided to use [spaCy](https://spacy.io/) to map words into their [lemma](https://en.wikipedia.org/wiki/Lemma_(morphology)). Doing it in Spark was difficult for reasons explained [in this blog post](https://haridas.in/run-spacy-jobs-on-apache-spark.html), so I decided to dump all data and use spaCy on batches of the data.

I spent a few hours debugging writing to disk because of [a Spark error that only affects Windows](https://stackoverflow.com/questions/40764807/null-entry-in-command-string-exception-in-saveastextfile-on-pyspark/40958969). The dump ended up in 44 files. It took 10 mins and 30 secs to run spaCy on one file.

---
Last updated January 18 2021

Comments on this text? [Create an issue on Github!](https://github.com/Sti2nd/sti2nd.github.io/issues)