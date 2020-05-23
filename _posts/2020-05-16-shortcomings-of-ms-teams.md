---
layout: post
title:  "Shortcomings of Microsoft Teams"
description: "What I miss in Teams compared to other comm. tools"
date:   2020-05-16 19:37:00 +0100
categories: []
tags: [thoughts, opinions, microsoft]
permalink: /shortcomings-of-ms-teams/
lang: en_GB
author: "Stian Jørgensrud"
---

I use [Microsoft Teams](https://www.microsoft.com/en-ww/microsoft-365/microsoft-teams/group-chat-software) at work, and this little post is where I explain how it could be better (for me). The communication tools I am comparing MS Teams to are the ones I have used and is fit for business; Skype and [Slack](https://slack.com/).

Mostly I am comparing with the good one, Slack. I will write Teams when meaning MS Teams from now on.

## Bad keyboard shortcuts and no custom shortcuts

From the beginning when my company switched to Teams, I missed the keyboard shortcuts from Slack. As a developer I am used to keyboard shortcuts; I have actually started to love keyboard shortcuts, and I am using them more and more. MS Teams does have keyboard shortcuts, but they differ from the other communication apps, and there are no option to customise them. Learning different keyboard shortcuts for all the different software I use, is simply not feasible!

Luckily for us today, many programs have adopted the same keyboard shortcuts! ❤ Copy and paste is perhaps the most famous example of functionality that transcends most programs, and they almost always have the same keyboard shortcuts: `CTRL + C` and `CTRL + V`. Some of the reason that they have been "standardized", is probably because the operating systems offer this functionality with the corresponding keybinding. So any app that utilises the OS' built in copy-paste will also probably use the OS' keybindings for those features. Now Teams, of course, utilises the OS' keybindings for the simple universal features. However, Teams is built on another infrastructure called [Electron](https://www.electronjs.org/), and it has decided to override numerous keybindings from Electron!

[Electron](https://www.electronjs.org/) is built on [Chromium](https://www.chromium.org/Home), so basically Electron by default uses the same keybindings as the Chrome browser. And we know that Chrome has dominated for some time which means its keybindings is widely known. `CTRL + K` is for example the keyboard shortcut that focuses the search bar and let you search, but in Teams it is `CTRL + E`. `ALT + LEFT_ARROW` is the command to go back in Chrome, and in Teams they simply decided to turn the keyboard shortcut off but still have the feature??? `CTRL + K` is the command to open the Quick Switcher in both Slack and Discord, and like I just said, the nearest thing we have are probably `CTRL + E`, which I don't usually remember. Even more funnier is that Slack and Discord is also based on Electron, so Teams is definitly the weird guy.

### User voice

Lacking good keyboard shortcuts made me so annoyed that I wanted to give Microsoft feedback and I went to the [Microsoft Teams User Feedback Forum](https://microsoftteams.uservoice.com/) (mostly called UserVoice I believe). I upvoted some of the requests of custom keyboard shortcuts ([like this one](https://microsoftteams.uservoice.com/forums/555103-public/suggestions/33625345-change-keyboard-shortcut)), but they have so few votes that I don't think this feature will be implemented as a result of UserVoice anytime soon.

## Notifications not in notification centre

In bottom right corner of Windows lies the notification centre where apps can send their notifications. That's pretty neat, one place for all the notifications! For some reason Teams does not send its notification there... I find that extremely surprising! One would think that an app made by Microsoft would use the notification centre in the OS made by the same company.

## No markdown support

As a developer I write markdown every day! If I need to send a code snippet, or just a terminal command, how am I going to format it without markdown? With **three** mouse clicks it is possible, but I am trying to avoid using the mouse at all, here! I have found out that if one write three backticks on a new line ```, it starts a code block, but without the option of specifying the language.

## Few reactions and no custom emojis

Several people in my company were clearly disappointed that Teams did not allow for custom emojis. Even more people were dissapointed that there were only six emoticons allowed as reactions to posts and comments. Perhaps removing the option to sit at work and customising emojis is better for work productivity, but it is bad for company culture! I would say communication became 10% more boring. 😜 Not a very important feature, but nice to have.

## Conclusion

Teams is ok in general, but if you are an IT company some of your developers won't like it (meaning they cannot be as efficient as they want to be, so consider that cost before saving money on using Teams). Slack branded itself as created for developers, I guess Teams is created for a wider audience, and maybe first and foremost non-technical people. As a developer, it is sad that Microsoft is so GUI focused (again) with this app, cause I feel more efficient with keyboard shortcuts and commands.

---

Comments on this text? [Create an issue on Github!](https://github.com/Sti2nd/sti2nd.github.io/issues)
