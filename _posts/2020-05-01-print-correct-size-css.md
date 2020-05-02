---
layout: post
title:  "Printing correct size using CSS"
description: "How to print using absolute units in CSS."
date:   2020-05-01 12:35:00 +0100
categories: []
tags: [CSS]
permalink: /print-css-correct-size/
lang: en_GB
---

On one personal project of mine I wanted to print a box (a HTML div) on paper with the specific dimensions 32mm x 35mm. Said again a little differently, I wanted the box on the paper to be 32mm x 35mm in our real physical world. And, I wanted to use CSS to design that box.

The first thing that comes to mind is that it would be nice if one could just tell CSS that the width is 32mm and the height is 35mm. Turns out, you can! CSS actually supports `mm` as a unit, so let's use it.

Measuring my laptop screen the dimensions were off. I thought it perhaps would solve itself when printing. It turns out, it didn't. Did I do anything wrong? What is the purpose of the CSS units `in`, `cm` and `mm` if they don't match the standardization (the International System of Units)?

You can read my [post about the absolute units in CSS]({% post_url 2020-05-01-5cm-css %}) to understand why the dimensions were off on my low-dpi screen. As for the print-out, I did do something wrong in my code. For printing, the absolute units in CSS should work perfectly!

![It was me all along](/assets/bug_meme.jpg "It was me all along")

This was just a heads up that if your print of CSS isn't correct you should probably debug the project code you wrote.

If you believe there is something wrong outside your code I suggest printing the following page and measure that the box is indeed 5cm tall and wide.

```html
<!doctype html>
<html>
  <head>
    <style type="text/css">
        div {
          border: 1px solid black;
          width: 5cm;
          height: 5cm;
        }
    </style>
  </head>
  <body>
    <div></div>
  </body>
</html>
```

---
_Last updated May 1 2020_
