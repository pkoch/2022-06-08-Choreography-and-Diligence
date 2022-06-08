---
title: Choreography and Diligence
description: Why microservices by default isn't a great bet.
author: Paulo Köch <hi@pko.ch>
url: https://pko.ch/talks/2022-06-08-Choreography-and-Diligence/
style: |
    img[alt~="bottom-right"] {
      position: absolute;
      bottom: 1rem;
      right: 1rem;
    }
---

# Choreography and Diligence

Why microservices by default isn't a great bet.

---

## tl;dr

- Microservices are better at making problems obvious then solving them.
- Packages can be a less demanding alternative.

---

# Ad hominem

Paulo Köch - <https://pko.ch/> <!-- I've been programming for 15 years, and I've worked in enough different environments with microservices. -->

- Yelp
  - Big company: ~400 engineers
  - Decade-old monolith, lots of microservices
- Doist
  - Medium company: ~50 engineers, ~10 backend, ~10 other contributers
  - Decade-old monolith, a few microservices
- Trust Fractal
  - Small company: ~10 engineers
  - Greenfield, lots of microservices

---

# Messy Monolith
<!-- A bunch of people wrote a bunch of code, and now they're sad about it. -->

## Nightmares

- Huge codebase <!-- - Just too much to know, it's nearly impossible to know the whole system. -->
- Separation of concerns <!-- - Everything's tangled up, there's unrelated wires everywhere because "I need to do an `if` over there", nobody knows where their part of the system ends and others' begin. Even worse, some improvident enterprising soul started using shared mutable state in memory. -->
- Deploying <!-- - Everyone wants to get in on releases, you're taking very unrelated changes to prod at the same time, there's a lot of waiting for gigantic test suites to pass, a whole new 500MB Docker image needs to go out all servers when you only changed a few bytes, etc. -->
- Scaling <!-- - Your frontpage is being hammered, you can't bill clients anymore. -->
- Bulkheading <!-- - Somebody misconfigures something about taxes, you can't show your homepage anymore. -->

&nbsp;

Let's make them impossible!

---

# Microservices!

![bg fit right:63%](clippy.png)

---

<!-- Microservices help with some things, and get in the way with others. -->
Engineering is about **trade-offs** and optimization.
<!-- It's also about feasability, but that doesn't apply to software. -->

---

# Microservices are: trade-offs

## Runtime

<!-- + You now have different parts of the application with their own databases, web workers, background workers, etc. You can scale precisely to what the customers need from you right now! -->
- Scale to your own needs
- You're now a distributed system
<!-- - Distributed systems aren't to be taken lightly. They're their own specialization inside backend. If you don't take it seriously, different parts of your system believe in different truths. -->

You can service requests in whichever way you want, but some team you never
heard of can take your service down.
<!-- - Your store service doesn't work because the inventory service doesn't work. -->

---

# Microservices are: trade-offs

## Tech

<!-- + If you have a scheduling problem, you can use Prolog! If you have a CPU-heavy problem, you can use Rust! -->
- Use the right tool for the job
- Expertise is fragmented
<!-- - Everyone produces CSV files slightly differenly. -->
<!-- - You're now on call for your microservices. If someone downstream from you is having problems, you now need their help or learn their system. Your dependency tree can be arbitrarily deep. -->

You can use Prolog in your microservice, but debugging is done through
committee.

---

# Microservices are: trade-offs

## Structure

<!-- + Nobody will feel tempted to pass unrelated information through your code. You control how much impact observability has in your performance. -->
- Other teams won't impact your internal structure
- Any externally-visible structure change becomes a coordination concern
<!-- - Removing a field from an API takes many quarters. Once you start emitting a stream of events in a certain schema, you're potentially locked to it forever. -->

Nobody can make your code slow or clunky, but now you need to have a
mailing list of downstream consumers to change your API.

---

# Microservices are: trade-offs

## Customs

- Freedom to choose your own philosophy
- Everyone needs to be onboarded

You can have monoids of endofunctors and algebraic effects, but only the
indoctrinated will help you.
<!-- The reverse is also true: if you want to contribute a change to somebody else's code, you need to learn their customs first. -->

---

# Microservices are: trade-offs

## Scope

<!-- + Only one concern, scope creeps start smelling pretty fast. -->
- Have tight codebases that do one thing right
- Have many services with various degree of overlap
<!-- - Different systems will have different assurances. -->
<!-- - When people can't convince someone to add a feature to some sevice, they might very well fork it and implement that thing in the new fork. -->
<!-- - Eventually, you'll have to adopt governance to decide when to sunset them. -->

You can always spin up new services, but eventually some are left running
with no consumers.

---

# Microservices are: hard boundaries

- The same people and functionality will still be connected.
- You've gone from razor-thin to concrete-thick boundaries.
- Conway's law and Inverse Conway maneuvers
- Teams have their own backlogs and schedules.
- Everything becomes choreography.
<!-- - The problem was "other people" and "code". It's still that. -->
<!-- - It's going from living in a loft to living in a campus. -->
<!-- - Much more tech involved. Don't pay for it unless you're also reaping tech benefits. -->
<!-- - Nobody wants to becomes an expert on distsys, DBs, k8s, and everything. -->
<!-- - You start concentrating competency (both tech and domain) on teams. -->
<!-- - You can outsource to both services and consultancy. -->
<!-- - Microservices shifts the focus to teams and their stewardship. -->

---

# - Everything becomes choreography.

&nbsp;

---

# - Everything becomes choreography.

Choreography is the new nightmare.

---

# Moving on

Microservices is linking at the network layer.

How about we try linking at the function level?

---

# Packages!

---

# Packages are: the classic commodities

- Scale arbitrarily
- Harder boundaries than a single codebase
- Softer boundaries than multiple systems
- Fully supported and made easy by your ecosystem (hopefully)
<!-- - It's going from living in a loft to living in an apartment. -->

---

# Packages are: trade-offs

## Runtime

<!-- - Your store can DoS your homepage. -->
- Constrained to the same process space
- Not a distributed system
<!-- + No more timeouts, retries, sagas, or eventual consisteny. -->

---

# Packages are: trade-offs

## Tech

<!--
You can still import alien code through JNI, FFI, dynamic libraries, etc. But
you're now constrained to your ecosystem. Like Erlang? Too bad! JNI takes a
bunch of time on the first run? Too bad! Need to translate the in-memory
representation at the boundary? Too bad!
-->
- Contained to one ecosystem
- Expertise is shared and compounded
<!--
This essentially means there's only a single "language plarform" team.
-->

---

# Packages are: trade-offs

## Structure

<!-- - It's easier to forgive a dumb argument in a function call than in an HTTP call. -->
- Everyone needs to be dilligent about boundaries
- Chaging APIs in a codebase is a well-solved problem
<!-- - It's also easier to undo. -->

---

# Packages are: trade-offs

## Customs

- You need to comply to some practices
- Onboarding is much cheaper

---

# Packages are: trade-offs

## Scope

- It's hard to understand which part of the codebase should do what
- There's lots of mature tooling to help you navigate

---

# Modular Monolith!

---

# Modular Monolith

## Nightmares

- Huge codebase
- Separation of concerns
- Deploying
- Scaling
- Bulkheading

&nbsp;

We still need to get out of them.

---

# Modular Monolith: nightmares

## Huge codebase

- Factor parts out to packages
- Laborious, but easy

---

# Modular Monolith: nightmares

## Separation of concerns

- Be diligent about architecture
- Laborious, **not** easy

---

# Modular Monolith: nightmares

## Deploying

- Focus on package bumps
- Automatable, and easy

---

# Modular Monolith: nightmares

## Scaling

- Use per-endpoint process pools
- Automatable, and easy

---

# Modular Monolith: nightmares

## Bulkheading

- Be diligent about process-level globals and in-process dependencies
- Light-touch, **not** easy

---

# Modular Monolith: what's not easy

- Be diligent about architecture
- Be diligent about process-level globals and in-process dependencies

---

# - Be diligent

&nbsp;

---

# - Be diligent

Diligence is the new nightmare.
<!-- In microservices, this was being enforced by other teams. -->

---

# Engineering is about trade-offs and optimization

## Choose the lesser evil

What's easier to optimize in your context?

- Choreography: go through the motions for **all** dependencies
- Diligence: educate and commit yourself and **all** your peers

## Intrinsic complexity isn't removable, only focusable

> *What makes you think you're not going to make a mess out
> of \[microservices\]?*
> -- Kevlin Henney, [Managing Complexity in Software](https://youtu.be/P7CfWtR-ECk?t=1371)

![bottom-right](./microservices_mess.png)

---

# Thank you

## <https://pko.ch/talks/2022-06-08-Choreography-and-Diligence/>

![bottom-right](./self.png)
