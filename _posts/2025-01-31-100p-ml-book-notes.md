---
layout: post
date: 2025-01-31
title: Book notes - "The Hundred-Page Machine Learning Book"
tags: ai-ml
last_updated: 2025-02-02
status: init
type: note
---

Notes taken while reading [The Hundred-Page Machine Learning Book](https://themlbook.com/) by Andriy Burkov. Some notes are directly from the content of the book, some are for related concepts from across the web, some are my own interpretation. Not exhaustive.

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
- These are not ML algorithms, but the solvers of minimization problems.
- Function to minimize has a gradient in most points of its domain.

---

Algorithms that build the model using the whole dataset at once:
   - Decision tree learning
   - Logistic regression
   - SVM

---

Algorithms that can be trained iteratively one batch at a time:
  - Naïve Bayes
  - Multilayer perceptron
  - SGDClassifier/SGDRegressor
  - PassiveAggressiveClassifier/PassiveAggressiveRegressor

---

Algorithms that can be used for both classification and regression:
  - SVM
  - kNN