---
layout: post
date: 2025-01-31
title: Book notes - "The Hundred-Page Machine Learning Book"
tags: ai-ml
last_updated: 2025-01-31
status: init
---

Notes taken while reading [The Hundred-Page Machine Learning Book](https://themlbook.com/) by Andriy Burkov. Some notes are directly from the content of the book, some are for related concepts from across the web, some are my own interpretation.

---

### Building blocks of a learning algorithm

1. a loss function
2. an optimization criterion based on the loss function
3. an optimization routine leveraging training data to find a solution to the optimization criterion.

---

For many models, the optimization criterion is convex, which means:
   - every local minimum is a global minimum
   - the optimal set is convex
   - if the objective function is strictly convex, then the problem has at most one optimal point.
(reference: [Wikipedia](https://en.wikipedia.org/wiki/Convex_optimization#Properties))

---

Gradient descent and stochastic gradient descent are most frequently used optimization algorithms when the optimization criterion is differentiable.