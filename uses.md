---
layout: page
title:  "Uses"
description: "Notes on everything I use for programming"
permalink: /uses/
lang: en_GB
---

Notes on everything from the editor and terminal I use, to my git aliases. I wrote this page mostly as notes for myself, and was also inspired by [uses.tech](https://uses.tech/), a web page with links to other developers that describe what (setups, gear, software and configs) they use.

## OS

Windows

- With Windows Subsystem for Linux (WSL) turned on, so I get Bash. I rarely actually use WSL, but sometimes one need the real deal.

Used Linux (Ubuntu) a bit before.

## Shells

Git Bash that comes with [git](https://git-scm.com/) installations on Windows.

I know how to navigate in cmd, but try to avoid it.

### Functions

- [z](https://github.com/rupa/z) So I can autocomplete paths I have visited recently and frequently.

## Terminals
  
- Mintty (the default with Git Bash)
- Visual Studio Code. I often like to run shells inside the editor.
- Windows Terminal

When Windows Terminal reaches version 1 I suspect I will try to always use it instead of Mintty.

## Editor / IDE

[Visual Studio Code](https://code.visualstudio.com/). Pretty much use it for everything possible. Also use the command `code FILE_OR_LOCATION` to lauch VS Code from terminal.

### Extensions

- [Prettier](https://prettier.io/) for formatting
- [GitLens](https://gitlens.amod.io/) with pretty much everything turned off except Status Bar blame and Repositories View (which I show inside the Source Control side bar). Remember to disable GitLens keyboard shortcuts by adding `"gitlens.keymap": "none"`. [eamodio/vscode-gitlens#1004](https://github.com/eamodio/vscode-gitlens/issues/1004).
- [Remote - WSL](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl) to allow VS Code to run inside WSL.
- [Visual Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.vscodeintellicode)
- [Auto Rename Tag](https://github.com/formulahendry/vscode-auto-rename-tag)
- [Add jsdoc comments](https://marketplace.visualstudio.com/items?itemName=stevencl.addDocComments) So I can start writing `/**` and autocomplete a jsdoc.
- [Polacode](https://marketplace.visualstudio.com/items?itemName=pnp.polacode) for high resolution screen shots of code (for presentations)
- [Split Lines](https://marketplace.visualstudio.com/items?itemName=brainfit.split-lines) to add line breaks in the middle of a string without hassle.
- And more extensions based on the tech I use on the project; like language servers, linters, syntax highliters and validators.

### Themes

- Dark+ (the default)
- [One Dark Pro](https://marketplace.visualstudio.com/items?itemName=zhuangtongfa.Material-theme)

## Git aliases

- [git last](https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases) to be able to see last commit
  - Add it with: `$ git config --global alias.last 'log -1 HEAD'`

## Keybindings

For all programs I try to stick with the same keybindings as in Chrome. Also picked some up from Eclipse (I guess), and now from VS Code.

| Shortcut | Function |
| --- | --- |
| CTRl + T | Open new tab / open file in project |
| CTRL + W | Close current tab |
| CTRL + SHIFT + T | Open last closed tab |
| CTRL + TAB | Go to next tab |
| CTRL + SHIFT + TAB | Go to previous tab |
| ALT + LEFT_ARROW | Go back (to last edit location) |
| ALT + RIGHT_ARROW | Go forward (to next edit location) |
| ALT + DOWN_ARROW | Move line down |
| ALT + UP_ARROW | Move line up |
| CTRL + D | Delete line |
| CTRL + SPACE_BAR | Autocomplete |
| CTRL + SHIFT + P | Search in program functionality |
| CTRL + N | Create new file |
| CTRL + SHIFT + N | Create new folder |

Note to self: perhaps I should switch to `CTRL + P` to open file in project instead of `CTRL + T`, since `CTRL + P` is standard in Chrome Devtools and VS Code.

### The universal keybindings

| CTRL + C | Copy |
| CTRL + V | Paste |
| CTRL + X | Cut |
| CTRL + Z | Undo |
| CTRL + Y | Redo |
| SHIFT + SCROLL | Scroll horizontally! I am looking at you Visual Studio 😡 |

## Other

### Password manager

[LastPass](https://www.lastpass.com/). You gotta have one if you want to remember your passwords AND have strong passwords!
