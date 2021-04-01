---
layout: post
title:  "Creating an Alias game online"
description: "Creating online Alias, a game similar to Taboo"
date:   2021-04-01 21:39:00 +0100
categories: []
tags: [game, big data, data analysis, creation, javascript, react, analyse]
permalink: /also-known-as-game/
lang: en_GB
image: /assets/Alias_online.png
author: "Stian Jørgensrud"
---

> For å spille Alias følg denne linken: [stianjo.no/also-known-as](https://stianjo.no/also-known-as/)

There are many variations of the game where a team is guessing a word only one team member knows. One such game is [Alias](https://en.wikipedia.org/wiki/Alias_(board_game)) from Tactic, and this game is well known in Norway. I searched for an online implementation of it one time, and found nothing. (For English speakers I guess [say-another-way.online](https://say-another-way.online/) is a fully digital version you could try). I want it in Norwegian, and it doesn't need any rules implemented; just the cards with some words on is ok!

To create a word game we need some words. I thought about using a dictionary, but that contains too many advanced words. I knew it is possible to count the frequencies of words on Wikipedia, and decided that the top words would be words well known and hopefully suitable in a game of Alias. Wikipedia actually have a list of the most frequently used words [on this link](https://en.wiktionary.org/wiki/Wiktionary:Frequency_lists/Norwegian), but I didn't know that at the time... This require some serious over-engineering!

## Mining Wikipedia for words

I read the official [download page](https://en.wikipedia.org/wiki/Wikipedia:Database_download) and first downloaded `nowiki-20210101-pages-articles.xml`. Since neither [pandas](https://pandas.pydata.org/) nor [Apache Spark](https://spark.apache.org/) can import XML out of the box, I decided to go for json format instead. After some trying and failing with converting [Wiki text](https://en.wikipedia.org/wiki/Help:Wikitext), I found that the [CirrusSearch option on this page](https://dumps.wikimedia.org/other/) is a json dump with expanded Wiki text. So I ended up downloading `nowiki-20210111-cirrussearch-content.json.gz`.

I quickly confirmed that Python could not import the entire JSON file in memory, which was what pandas tried to do. Something beefier is [Apache Spark](https://spark.apache.org/), and I chose it simply because I had used it before. It is supposed to be a tool one can use on your standard off-the-shelves computers for Big Data. Since it is meant for large data, it means it will store data on the disk instead of in memory. And it of course supports parallelism. Although the real power comes from the ability to run in a cluster, I will just use my single computer.

I used Jupyter notebook for the analysis, and you can read the notebook with text and code [at Github](https://github.com/Sti2nd/alias-online/blob/main/words/Mining%20Wikipedia%20for%20words.ipynb); it will actually render it for you!

I spent some hours cleaning the data. Although the dataset didn't contain wiki text, there were still some templates which made appearance as common words and phrases. These templates I gave up removing.

I decided to use [spaCy](https://spacy.io/) to map words into their [lemma](https://en.wikipedia.org/wiki/Lemma_(morphology)). Doing it in Spark was difficult for reasons explained [in this blog post](https://haridas.in/run-spacy-jobs-on-apache-spark.html), so I decided to dump all data and use spaCy on batches of the data. I spent a few hours debugging writing to disk because of [a Spark error that only affects Windows](https://stackoverflow.com/questions/40764807/null-entry-in-command-string-exception-in-saveastextfile-on-pyspark/40958969). The dump ended up in 44 files. It took 10 mins and 30 secs to run spaCy on one file. In total it took around 8 hours to run on all files, so it is highly unoptimised!

Not surprisingly, the top words were just [stopwords](https://en.wikipedia.org/wiki/Stop_word). I ended up removing both English and Norwegian stopwords. The top 10 words ended up being these:

```text
besøke
norsk
mye
annen
under
to
artikkel
få
hos
år
```

If we compare with the [Frequency list on Wikipedia](https://en.wiktionary.org/wiki/Wiktionary:Frequency_lists/Norwegian), there are some of the same words on top. The list on Wikipedia has not removed stopwords, it is from 2011, and it seems it has not performed lemmatisation either. On top 250 of the Wikipedia list we find different inflections of the word "artikkel" (article), which could explain why I have artikkel in top 10.

Some limitations with my list (top 1000) are:

1. I didn't remove the templates, and I strongly suspect the templates have skewed the result. For example I believe "wikipedia", "wikispecies", "wikimedia" and "commons" are mentioned in many templates, and they will thus have been counted more than they should.
2. I didn't manage to preserve big capital letter in names and places. These are uncommon to have in an Alias game, so ideally I should have removed them.
3. It contains random English words.
4. It contains all the months, and probably a lot the number words.

The three first limitations I find hard to fix in code, which is why I just will accept this list and use it in the game. I manually removed the English words I found as well as the Wikipedia specific ones.

## Creating the UI

Using React with TypeScript, I created a simple UI with swipable cards. The code can be found [on Github](https://github.com/Sti2nd/also-known-as) and you can play it (in Norwegian only) on [stianjo.no/also-known-as/](https://stianjo.no/also-known-as/).

![Alias online image of phone](/assets/Alias_online.png)

---
Last updated April 1 2021

Comments on this text? [Create an issue on Github!](https://github.com/Sti2nd/sti2nd.github.io/issues)