---
layout: post
title:  "How to create a custom Guess Who game"
description: "Custom Guess Who game with React"
date:   2020-05-23 19:03:01 +0100
categories: []
tags: [makerspace, hackerspace, creation, javascript, react]
permalink: /custom-guess-who-game/
lang: en_GB
image: /assets/custom-guess-who-game/norwegian-guess-who-game.jpg
author: "Stian Jørgensrud"
---

A colleague told me that a custom [Guess Who](https://en.wikipedia.org/wiki/Guess_Who%3F) game was one of the best gifts he had given to his girlfriend. He swapped out the cards with images of family and friends and said it was a ton of fun to play. I was inspired to create one for my girlfriend's birthday. This post explains how I created a custom Guess Who game using [React](https://reactjs.org/), and here's a [link to the repo with the code](https://github.com/Sti2nd/custom-guess-who) so you can create your own!

![Norwegian version of the Guess Who game](/assets/custom-guess-who-game/norwegian-guess-who-game.jpg)

Reading this text is not necessary to use the [Custom Guess Who game repository](https://github.com/Sti2nd/custom-guess-who). To create your own simply:

1. Buy a version of the Guess Who game
2. Find 24 images of people and crop them to their heads
3. Use the code I have provided to generate the cards
4. Print the cards, cut them out and play!

## Planning

I knew I needed a Guess Who game, so I ordered it right away. The bigger problem was how to create the cards. A card in the game consist of:

- an image of a head
- a text (the name of the person in the image)
- a background colour

One option was to use an image editor to create each card in its correct size, and then paste all of the cards into a document and print them. Since there are in total 72 cards in the game, I believed the manual labour in this approach would be too much. Another option was to create the cards in the physical world by cutting out the cards in the correct size, and then glue the image on and write the name. Again, I believed this approach would require too much manual labour. I enjoy the craft of programming, and programming can often reduce repeated manual labour, a perfect fit! I decided to use my front end skills with web technologies to automate as much as possible of the card creation.

## Creating the cards in React

In the game, there are 24 different images, and each image appear on three cards. Given the repetetive nature of the problem, a component based UI library was an obvious choice. I decided to use React, simply because I knew it from before. There were two types of cards; one type for the players and one type called secret cards. I created one component for each of the card types.

It was essential that the size of the cards were correct when I printed them, so they would fit the game's card containers. Luckily, CSS actually supports the unit `mm` which will ensure the print out is correct when printed. Using web technologies to design the cards was almost easier than I first thought! In reality, I used some time on checking that the print out indeed had the correct size. When measuring the cards on the screen, they didn't have the correct size. While you can read in another blog post of mine that the [absolute units in CSS may not render in correct size on low-dpi screens]({% post_url 2020-05-01-5cm-css %}), the reason was simply a silly mistake by me.

With cards in their correct size and colour, they were ready to be filled with content. Instead of hard coding the path to all images and the names of each person, I imported all images from a folder and use the filename (minus the file extension) as the name to be displayed. One thing I did have to hard code was the number of printer pages because neither Flexbox nor CSS Grid supports being printed over several pages.

*The only good explanation of why Flexbox and CSS Grid doesn't break over pages, that I have found, is this [Chromium issue from 2015](https://bugs.chromium.org/p/chromium/issues/detail?id=473481) where it is stated that the CSS spec does not specify how to make them break over pages. From the [spec of 2018](https://www.w3.org/TR/css-flexbox-1/#pagination) however, as I read it, it seems page breaks inside a Flexbox container should be supported. If you know something about this, do tell!*

## The finale

The rest of the job was to find 24 pictures of friends and family and crop them to their heads. Then I could simply add them all to a folder, and voilà, four pages with cards ready to be printed! The following picture illustrates how one image will be rendered into three cards with names.

![Screenshot of the Guess Who React app](/assets/custom-guess-who-game/guess-who-chrome-screenshot.png)

The end result turned out pretty good, and more importantly, the gift receiver was happy!

---

Comments on this text? [Create an issue on Github!](https://github.com/Sti2nd/sti2nd.github.io/issues)
