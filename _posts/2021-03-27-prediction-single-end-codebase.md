---
layout: post
title:  "Prediction: front- and back end, same codebase"
description: "I predict that one developer can more easily create both front- and back end in the future"
date:   2021-03-27 16:14:00 +0100
categories: []
tags: [prediction, front end, back end]
permalink: /single-end-codebase/
lang: en_GB
author: "Stian Jørgensrud"
---

I was just thinking about the current practice of writing front end and back end code separately, and I wouldn't be surprise if that is starting to change. Evolution in software development seems like an endless circle of getting a new advanced feature and then making it easier to use. At consultant firms in Norway for the last 10 years, I believe it was common to deliver a back end in Java/C#, and a front end in JS. The benefits of having a dedicated back end can be many; I can mention security and performance as two factors. The benefits of writing one codebase is that it potentially can be much faster, and increased productivity has been the winning factor for hundreds of years. My realisation is that having back end and front end (running on two different machines) isn't a hinder for having one codebase. When I write "one codebase" in this post, I don't mean that it is an application running solely on a client or on a server. Just running code on one of the sides (client or server) is a completely viable solution for many problems and to ensure one codebase, but in this post I argue that it is possible to have one codebase running on both sides.

We developers could be writing one codebase that ends up running a back end on a server and a front end on the client. The codebase we write could simply be compiled into a back end part and a front end part. I argue that the connection between front end and back end is boiler plate. For networking, we follow some standard like [REST](https://en.wikipedia.org/wiki/Representational_state_transfer) or [GraphQL](https://graphql.org/). Since those standards have become so extensive and there are many best practices, it is possible to auto-generate code for them. We developers should be able to just deal with one codebase and at the same time have the exact same benefits as today with separate code bases for front end and back end. In theory, it is possible.

I think the trends are also pointing in the direction of a single codebase. GraphQL has proven that back end doesn't necessarily need extensive logic to prepare data for the front end. Some low-code, no-code, CMS and CRM solutions lets you develop without thinking about where front end ends and back end begins, they handle them both in the background! [React Server Components](https://reactjs.org/blog/2020/12/21/data-fetching-with-react-server-components.html) is a very new technology that would allow React to exist on the back end and front end simultaneously. These are just meant as examples of the trend; blurring the lines between front end and back end.

I want to mention that single codebase is not new. Most of us have used PHP pages that are server side rendered but still executes some JS client side. This single codebase trend I predict is just a part of the endless circle; getting new features, and then making them easier to use.

What do I mean with the word "code base"? It could be one programming language in the same repo, or it could be one low-code or no-code solution. What I do think, is that running a back end and a front end is a tested and proven solution that we will keep, at the same time as we developers will get tools that makes it easier for us to develop both. At some point, the tools will blur the lines so much that we will think of front end and back end as just another implementation detail.

---

Comments on this text? [Create an issue on Github!](https://github.com/Sti2nd/sti2nd.github.io/issues)
