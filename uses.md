---
layout: page
title:  "Uses"
description: "Notes on everything I use for programming"
permalink: /uses/
lang: en_GB
---

Notes on everything from the editor (IDE) and terminal I use, to my git aliases. I wrote this page mostly as notes for myself, and was also inspired by [uses.tech](https://uses.tech/), a web page with links to other developers that describe what (setups, gear, software and configs) they use.

## OS

Windows

- With Windows Subsystem for Linux (WSL) turned on, so I get Bash. I rarely actually use WSL, but sometimes one need the real deal.

Used Linux (Ubuntu) a bit before.

## Shells

- Git Bash. A shell that comes with [git](https://git-scm.com/) installations on Windows. This is my default shell.
  - Supports the common [Bash commands](https://en.wikipedia.org/wiki/List_of_Unix_commands)
  - Has built in [SSH capabilities](https://en.wikipedia.org/wiki/SSH_(Secure_Shell))!
  - Doesn't support CTRL + ARROW keybindings, but you fix this by following 
- [PowerShell Core](https://www.microsoft.com/store/productId/9MZ1SNWT0N5D)

### Functions

- [z](https://github.com/rupa/z) So I can autocomplete paths I have visited recently and frequently.

## Terminals
  
- [Windows Terminal](https://www.microsoft.com/store/productId/9N0DX20HK701). Can show different shells in tabs (just like ConEmu).
- Visual Studio Code. I often like to run shells inside the editor.
- Mintty (the default with Git Bash)

## Editor / IDE

1. [Visual Studio Code](https://code.visualstudio.com/). Pretty much use it for everything possible. Also use the command `code <FILE_OR_LOCATION>` to lauch VS Code from terminal.
2. Visual Studio. Sometimes have to use it for work. Start it from terminal with `start devenv`
3. IntelliJ. Sometimes have to use it for work. After adding `C:\Program Files\JetBrains\IntelliJ IDEA 2019.2.4\bin` to PATH, one can start it from terminal with `idea64.exe <FILE_OR_LOCATION> &`. The trailing ampersand is to put the process in background

### Editor extensions

- [Prettier](https://prettier.io/) for formatting
- [GitLens](https://gitlens.amod.io/) with pretty much everything turned off except Status Bar blame and Repositories View (which I show inside the Source Control side bar). Remember to disable GitLens keyboard shortcuts by adding `"gitlens.keymap": "none"`. [eamodio/vscode-gitlens#1004](https://github.com/eamodio/vscode-gitlens/issues/1004).
- [Remote - WSL](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl) to allow VS Code to run inside WSL.
- [Visual Studio IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.vscodeintellicode)
- [Auto Rename Tag](https://github.com/formulahendry/vscode-auto-rename-tag)
- [Add jsdoc comments](https://marketplace.visualstudio.com/items?itemName=stevencl.addDocComments) So I can start writing `/**` and autocomplete a jsdoc.
- [CodeSnap](https://marketplace.visualstudio.com/items?itemName=adpyke.codesnap) for high resolution screen shots of code (for presentations)
- [Split Lines](https://marketplace.visualstudio.com/items?itemName=brainfit.split-lines) to add line breaks in the middle of a string without hassle.
- And more extensions based on the tech I use on the project; like language servers, linters, syntax highliters and validators.

### Themes

- Dark+ (the default)
- [One Dark Pro](https://marketplace.visualstudio.com/items?itemName=zhuangtongfa.Material-theme)

## Browser

- Chrome
- Firefox Developer. Sometimes one need another browser and Mozilla is cool.

### Browser extensions

- [JSON Formatter](https://chrome.google.com/webstore/detail/json-formatter/bcjindcccaagfpapjjmafapmmgkkhgoa)
- [Vimium](https://chrome.google.com/webstore/detail/vimium/dbepggeogbaibhgnhhndojpepiihcmeb) to be able to solely use the keyboard to navigate while browsing. Four of the shortcuts were enough for me, so I unbound the rest so I override as few as possible (for example the shortcuts on Github)
  - With the custom key mappings

    ```text
    # Insert your preferred key mappings here.
    unmapAll
    map j scrollDown
    map k scrollUp
    map f LinkHints.activateMode
    map F LinkHints.activateModeToOpenInNewTab
    ```

  - With scroll step `67px` for that snappy feeling without too much lag.

- [Full page screen capture](https://chrome.google.com/webstore/detail/full-page-screen-capture/fdpohaocaechififmbbbbbknoalclacl) if I need to screenshot a web page.

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
| CTRL + B | Build (the current project) |

Note to self: perhaps I should switch to `CTRL + P` to open file in project instead of `CTRL + T`, since `CTRL + P` is standard in Chrome Devtools and VS Code.

### The universal keybindings

Of course I also use these

| Shortcut | Function |
| --- | --- |
| CTRL + C | Copy |
| CTRL + V | Paste |
| CTRL + X | Cut |
| CTRL + Z | Undo |
| CTRL + Y | Redo |
| CTRL + F | Search |
| SHIFT + SCROLL | Scroll horizontally |

## Other

### Git aliases

- [git last](https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases) to be able to see last commit
  - Add it with: `git config --global alias.last 'log -1 HEAD'`
- `git fuck` to be able to undo the most common error I do, which is to commit on the wrong branch
  - Add it with: `git config --global alias.fuck 'reset --soft HEAD~1'`

Bonus tip: `git checkout -` checks out the branch you were on last.

### Password manager

[LastPass](https://www.lastpass.com/). You gotta have one if you want to remember your passwords AND have strong passwords!

### Windows Terminal settings

[Link to gist with settings.json for my Windows Terminal](https://gist.github.com/Sti2nd/07322bda4c450b77f33eb1f5cda1dd9a)

### Bash .inputrc

Paste the following in `~/.inputrc` Shamelessly stolen from [hellricer.github.io](https://hellricer.github.io/2019/05/21/ctrl-arrows-in-terminal.html), thanks!

```bash
### ctrl+arrows
# works in most terminals: xterm, gnome-terminal, terminator, st, sakura, termit, …
"\e[1;5C": forward-word
"\e[1;5D": backward-word
# urxvt
"\eOc": forward-word
"\eOd": backward-word

### ctrl+delete
"\e[3;5~": kill-word
# in this case, st misbehaves (even with tmux)
"\e[M": kill-word
# and of course, urxvt must be always special
"\e[3^": kill-word

### ctrl+backspace
"\C-h": backward-kill-word
```

---
Last updated December 12, 2022

Comments on this text? [Create an issue on Github](https://github.com/Sti2nd/sti2nd.github.io/issues)
