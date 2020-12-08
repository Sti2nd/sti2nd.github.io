---
layout: post
title:  "Developing MagicMirror on Windows"
description: "Using WSL to develop MagicMirror"
date:   2020-12-08 23:11:00 +0100
categories: [hackerspace]
tags: [wsl, windows subsysten for linux, magic mirror norway, raspberry pi, javascript, technical, makerspace, hackerspace, creation]
permalink: /developing-magic-mirror-wsl/
lang: en_GB
author: "Stian Jørgensrud"
---

I have been developing my custom modules for the [Magic Mirror](https://magicmirror.builders/) software on my old laptop. Windows is the operating system, but I have been using [Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/install-win10) (WSL) to develop it. I assume I didn't get it to run on Windows when I started, but [people have done it](https://forum.magicmirror.builders/topic/4089/complete-walkthrough-install-magicmirror-on-a-pc-windows-7-10) so I should try it out again soon. Anyway, on my old laptop I managed to run Magic Mirror in WSL 1, which I could not reproduce on my stationary... so for future reference, here is how I run Magic Mirror software on Windows in WSL 2.

## Magic Mirror in WSL 2

Follow the [official guide on how to install WSL 2](https://docs.microsoft.com/en-us/windows/wsl/install-win10).

Follow the [manual installation guide on Magic Mirror](https://docs.magicmirror.builders/getting-started/installation.html#manual-installation).

For me it failed on `npm install` with the error: `: not found.sh: 4:`. In this step it tried to run some sh scripts

```text
sh untrack-css.sh && sh installers/postinstall/postinstall.sh
```

the solution were simply to run these scripts as you would in your own shell. With Git Bash `./untrack-css.sh` for example.

Then it failed on `line 4: $'\r': command not found`. The solution for this were to change from Windows style line endings (CRLF) to Linux style (LF) before running the script again.

It then failed on `npm start` with `./run-start.sh: not found`. Solution was once again to change line endings to LF.
