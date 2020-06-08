---
layout: post
title:  "What is Webassembly"
description: "What is the deal with Webassembly?"
date:   2020-06-07 21:36:00 +0100
categories: []
tags: [technical, webassembly]
permalink: /what-is-webassembly/
lang: en_US
image: /assets/WebAssembly_Logo.svg
author: "Stian Jørgensrud"
---

Or rather, what is the deal with Webassembly? We already know JavaScript, CSS and HTML are used on the web, and there are tons of different libraries we can use. So what about WebAssembly?

In this text I simply write down what I know; could serve as a good introduction if you have barely heard of WebAssembly. 

*Text continues after the image*

![WebAssembly logo](/assets/WebAssembly_Logo.png "WebAssembly logo")

### WebAssembly is a new language for the web

For a long time it was true that JavaScript was the only programming language supported natively by the browsers. JavaScript has throughout the years had competitors like ActionScript (in Flash) by Adobe, Silverlight by Microsoft, and even Java, but none succeeded to replace JS as the native programming language of the web. That JavaScript has remained the de-facto programming language for the web doesn't mean it it perfect, of course. It has always been critized, and one area that JS has been critized for is its performance.

Because of the [browser wars](https://en.wikipedia.org/wiki/Browser_wars) the performance of JavaScript engines and thus JavaScript execution sped up, but JS was still critized for its performance. At Mozilla Foundation they discovered that if they wrote JavaScript code in a special limited way, the code could run faster; almost as fast as half native speed! They called this way of writing JavaScript for [asm.js](http://asmjs.org/), and it was intended to be a compilation target, not code developers wrote.

A few years after asm.js appeared, WebAssembly was announced. Instead of using JavaScript as the assembly language of the web, we actually got assembly for the web: [WebAssembly](https://webassembly.org/). This time, the goal was actual native speed. WebAssembly is like most assembly and like asm.js not intended to be written by developers, but to be a compile target. To use it one can write some code in C, for example, and compile it to WebAssembly. Then, in a web environment, one can for example call this code with JavaScript.

## The trick of the decade

So, suddenly all browsers decided to implement a new language for the web? Huge corporations have tried several times to get a new language to rule the web, and this times it simply worked? Seems weird that they didn't just implement an existing language, like C, when they were implementing a new language anyway? And this is where the genius lies!

One (and I am guessing the biggest) reason that JavaScript has not been tilted by the throne, is because it is the native programming language of the web. It works in all browsers out of the box. Even though Microsoft invented Silverlight to be able to write .NET languages in the browser, they still supported JavaScript in their browser (Internet Explorer)! And of course, when a lot of web pages used JavaScript, Internet Explorer couldn't stop supporting it without loosing a lot of the market.

WebAssembly is like Javascript also native. And the trick that made it possible, was to use the existing infrastructure: the JavaScript engines. Inspired by asm.js, WebAssembly is engineered to run on the JavaScript engines (with some minor changes probably), so the browser vendors did not have to spend huge efforts to implement it (relatively speaking, of course). According to a [blog post by Brendan Eich](https://brendaneich.com/2015/06/from-asm-js-to-webassembly/) WebAssembly was actually equivalent to asm.js in the beginning, which is smart to quickly make it native, and then it can diverge from JavaScript later to become even better.

## Applications

Applications for WebAssembly is everything that you need to be fast and do the heavy work. Data processing and games are two examples. You can call WebAssembly functions from JavaScript using the [WebAssembly JavaScript API](https://developer.mozilla.org/en-US/docs/WebAssembly/Using_the_JavaScript_API), so JS just became even more powerful. WebAssembly isn't meant to replace JavaScript, it (simply) fills a need for performance on the web.

And that is pretty much what I know! I have yet to actually use WebAssembly myself, but I will definitely consider it if I need to speed up a web application of mine a bazillion times.

---

Comments on this text? [Create an issue on Github!](https://github.com/Sti2nd/sti2nd.github.io/issues)
