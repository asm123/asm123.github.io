---
layout: post
date: 2025-02-05
title: Code is the Ultimate Documentation
tags: software-engineering
last_updated: 2025-02-05
status: init
type: article
---

In an ideal software engineering world, everything is well-documented and up-to-date. But the world is not ideal. 

Priorities change, pace changes, and documentation lags behind. Approved design docs get implemented differently. Tools get deprecated. Code moves around and code pointers from markdowns lead to dead links. READMEs become outdated.

**Therefore, code is the ultimate documentation.**

I do not mean it in the ["Good code is its own best documentation"](https://www.goodreads.com/quotes/9057917-good-code-is-its-own-best-documentation-as-you-re-about){:target="_blank"} way. 

I mean that the actual implementation is the only source of truth for how it actually works. Nothing else is as reliable.

Not the comment surrounding it, because the author of the comment may not have been able to articulate it clearly. I have seen a comment that explained a cryptic set of rules in triple negation. And yet, the rules that it hoped to describe turned out to validate the exact opposite.

Not the name of the function, because it may have been named with the utmost attention and yet missed a crucial detail. Imagine a method that says `MaybeSetSomething(...)`, but reveals nothing about when positive path of that maybe is triggered.

Not the name of enum because it may have been named considering a set of assumptions when it was first written, but now its usage may have expanded or shrunk and it is now a heavily used misnomer. I have seen an enum named with suffix `_BACKFILL` when it was first created 3 years ago, but now it controls important business logic for workflows which extend beyond backfills.

Not the name of the flag that controls the enablement of a feature because its name makes sense in the scope of one of the components of the launch, but there may have been multiple such flags on different layers which together decide what this flag is supposed to enable. Features touching multiple independent components are often guarded by a flag per critical component.

**Therefore, code is the ultimate documentation.**

> Note: The intent of this post is not to discourage documentation. A clear, up-to-date documentation saves a lot of time when reasonably reliable. *When reasonably reliable* is the key here.