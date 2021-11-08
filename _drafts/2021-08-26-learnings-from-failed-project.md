---
layout: post
title:  "Learnings from a failed project"
description: "Learnings from one project I was on"
date:   YYYY-MM-DD HH:MM:SS +0100
categories: []
tags: []
permalink: /learnings-from-failed-project/
lang: en_GB
image: 
author: "Stian Jørgensrud"
---

This is my notes on one of the projects

## About the project

*If we had known this at the beginning things would have gone better.*

- It was a large project
  - Multiple microservices
  - Multiple integrations with third parties
  - Third parties that the project was dependent on
  - Built on an existing codebase
- Was supposed to be delivered in short time
- New technologies and new infrastructure
- No specialists, just potatoes. Mostly juniors.

## Problems

Hard to say what is problems and what is side effects of problems in this section.

### Underestimated

The project was greatly underestimated. I am guessing the original estimate was 1/2 of the actual time and cost it should have been. Then there was scope creep that we continued to underestimate. Some reasons for this were perhaps

- Customer claimed it was a small system. In what must have been a quick and dirty planning phase the planned software was perhaps of medium size; a front-end, a back-end, and the back-end consisting of some microservices and some integrations.
- Believing new technology and infrastructure would cut the development time. Sure, this can be true in the long run, but when the project is already supposed to be done in a short time the overhead of learning new things eats up the time potentially saved. Also, new tech often have additional features compared to the old tech, features which often ends up getting used even though they wasn't considered essential in the old tech. These new features can be scope creep. Instead of saving time by using new tech one spend a bit more time and get more features. So the total amount of time spent developing features doesn't go down, but we do get more features per time spent. Overall I believe using new tech and infrastructure did not save any time. (The new tech could save some cost in the long run, though.)
- Believing building on an existing codebase would cut the development time. This can be true as well, but also comes with overhead in the beginning. We did not have anyone that worked on the existing codebase to learn from and the documentation was poor.
- Scope creep
  - The additional front end. What we didn't do when we estimated the additional front end, was to estimate how much work would be needed to be done in the back end because of this new front end. The project was hoping that the already planned APIs could be used for the additional front end as well, and a quick and dirty estimate was added to accomodate for changes that needed to be done and some extra routes. I believe that we greatly underestimated the increase in complexity from going from one to two clients. I wasn't even aware that an additional client would increase complexity at the time, so that is why I am writing it down now. Two clients have different needs, and so they might want to send in slightly different data and get slightly different data back. And if we look away from the obvious functional part, the clients was authorized differently which obviously adds more complexity.

### Juniors

In the beginning there were 2 seniors and around 6 juniors on my team. These numbers increased with mostly juniors. Juniors isn't a problem in itself but seem like a bad fit for an advanced project that should be delivered on short time.

### Scope creep

The most scope creep I have ever experienced. Since the project was supposed to be delivered in short time and supposed to be relatively small, naturally most details wasn't planned ahead. The project team (or those who planned) should take a lot of the blame here for not accounting more for the bad planning.

Since details had not been carved out, the customer did not know exactly what they needed, and more requirements were found constantly. Some of the requirements were entirely new features. For example, one large new feature was an additional front end. I was one of the people that estimated that front end, and that was basically how I joined the project.

Important third parties also constantly found new requirements, and seemingly more and more nearing the deadline since that was when we got down into the details. I know for a fact that some features were developed and then kind of scrapped because of new requirements from third parties.

### Poor project management

- Most people didn't know how to work! We had a process on paper, but not time to learn it except an hour where someone presented a Powerpoint.
- And since people didn't know the process, everything felt chaotic.
- Tasks were essentially vague and needed clarifications, but few knew how to get it. Also spending time on clarifying was time we didn't have.
- Setbacks and state of the software were not communicated to the customer.
  - Even though the project from my eyes was one month delayed after the first month, the customer was not told the delivery would be delayed until the week before the planned release.
  - At the time of the originally planned release the software was halfway finished at best.
- Security testing was performed by someone external to the project team a few weeks before the originally planned release date. The tester reported several flaws. We responded back that the flaws made sense, since we hadn't gotten to the point of implementing authentication and authorization yet...
- After the first delay the lack of understanding from management of the state of the software continued. The customer had essentially been told the delay was because of third parties, which indeed had caused some delay, and that my project team was delivering as promised. So at this point I belive the customer thinks the software is basically finished according to contract, and then it makes sense for the project team to keep adding new features to have something to do. Meanwhile, in reality we are only halfway and have already created technical debt worth the entire original project time.
- Management understood that we were delayed fairly early; because of the increased scope, mostly. So they added more people. Each month they added 1 or two new people. Very good that they added resources gradually, but the more people the more chaos and the less output per person. Management probably know all this too well, but the fact stands that 9 women cannot make a baby in one month. I would say the overhead before a new person on the project was up to speed was between 2 and 3 months; a large amount of time compared to the original plan. The big project organization of 30 people that we at one point reached produced the output of maybe 10 people in a longer running project.

### Bad methodology

The methodology we were supposed to work in has at least two downsides

- Difficult to learn (overhead). A process with overhead to learn was an especially bad fit for a project supposed to be short.
- Poor knowledge flow. Partly because of people not knowing and partly because of the tools used for documentation in the process.

### Skipping automatic tests

We just skipped writing automatic tests. Possible reasons:

- The short time is an obvious one. The management literally encouraged us to be sloppy when the deadline was nearing. "Better to go live with bugs than not go live" was something one would commonly hear from management and the customer.
- Juniors. I was not experienced in writing tests and thus was inefficient in writing them. Without examples from the seniors
- Bad QA. In the

## Some suggested solutions

Probably not every one of these suggestions could be used when doing a project fast, but I am not experienced enough to know which can be skipped.

### Plan the API before implementation

In order for developers to develop different parts of a system at the same time and be able to integrate it later they need to agree on something up front. I believe it is common to design the APIs that connects server with client before implementation. We ended up implementing several routes for performing the exact same operation. For example client 1 would call route 1 and client 2 would call route 2 and they would pass in the exact same data to the route which would essentially do the exact same operation.

### Be strict about API changes

In this project the different clients had different needs and introduced changes mid-implementation. It often turned out that each change in the client was a much bigger change (or addition) in the back end. I knew some of the changes could have been solved by doing two requests on the client instead instead of one. Sadly, we instead spent two weeks on simplifying it to one route on backend. Given that the back-end was way behind schedule, trading off backend-time for client-time was a bad decision. The people creating the API (like me) should have said no to several new routes and route changes.

Since we were poorly organized I am unsure if the right people (tech lead?) took a decision on these changes at all. In some cases I know the people working on the client told a random person working on server (like me) what their needs were and the changes was then incorporated without much thinking. If we should have been strict about API changes with the organization we had, all back-end people would have to know that they should be strict. Personally, as one of 10 junior developers in a large scale project I didn't feel at that time that I had the knowledge nor mandate to deny changes from the people working on the client.

### Better project management

Maybe it is possible to 

---
Last updated August 26 2021

Comments on this text? [Create an issue on Github!](https://github.com/Sti2nd/sti2nd.github.io/issues)
