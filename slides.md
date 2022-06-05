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

Paulo Köch - <https://pko.ch/>

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

Engineering is about trade-offs and optimization.

---

# Messy Monolith

## Nightmares

- Huge codebase
- Separation of concerns
- Deploying
- Scaling
- Bulkheading

&nbsp;

Let's make them impossible!

---

# Microservices!

---

Engineering is about **trade-offs** and optimization.

---

# Microservices are: trade-offs

## Runtime

- Scale to your own needs
- You're now a distributed system

You can service requests in whichever way you want, but some team you never
heard of can take your service down.

---

# Microservices are: trade-offs

## Tech

- Use the right tool for the job
- Expertise is fragmented

<!-- - You're now on call. -->

You can use Prolog in your microservice, but debugging is done through
committee.

---

# Microservices are: trade-offs

## Structure

- Other teams won't impact your internal structure
- Any externally-visible structure change becomes a coordination concern

Nobody can make your code slow or clunky, but now you need to have a
mailing list of downstream consumers to change your API.

---

# Microservices are: trade-offs

## Customs

- Freedom to choose your own philosophy
- Everyone needs to be onboarded

You can have monoids of endofunctors and algebraic effects, but only the
indoctrinated will help you.

---

# Microservices are: trade-offs

## Scope

- Have tight codebases that do one thing right
- Have many services with various degree of overlap

You can always spin up new services, but eventually some are left running
with no consumers.

<!--
Different systems will have different assurances. When people can't convince
someone to add a feature to some sevice, they might very well fork it and
implement that thing in the new fork.
-->

---

# Microservices are: eventually, commoditization

*Commoditization is the process of converting products or services into
**standardized**, marketable objects.*

Hard to avoid when involving data stewardship and more than a few hundred engineers.

---

# Microservices are: hard boundaries

- Not independence, a different type of dependence.
- Infra platform and language platform teams become a thing.
- Conway's law and Inverse Conway maneuvers
- Great for outsourcing competency!
- Everything becomes choreography.

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
- Focused on code, not stewarding data
- Fully supported and made easy by your ecosystem (hopefully)

---

# Packages are: trade-offs

## Runtime

- Constrained to the same process space
- Not a distributed system (no more retries or sagas!)

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

- Everyone needs to be dilligent about boundaries
- Chaging APIs in a codebase is a well-solved problem

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