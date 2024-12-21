---
layout: post
date: 2024-12-18
title: "[WIP] Notes - The unbearable slowness of being: Why do we live at 10 bits/s?"
tags: neuroscience
last_updated: 2024-12-18
status: 🌱
---

Source: [The Unbearable Slowness of Being: Why do we live at 10 bits/s?](https://arxiv.org/abs/2408.10234v2) - arxiv, found on [Hacker News](https://news.ycombinator.com/item?id=42449602)


## The paradox

Our senses gather data at `10^9 bits/s`, but our overall information throughput is only `10 bits/s`.

> The paradox: vast gulf between the tiny information throughput of human behaviour and the huge information inputs on which the behaviour is based.

## Measuring information rate of neurons

How to measure how much information a neuron conveys?
  1. Identify the range of outputs across all possible stimuli.
  2. Determine what part of that range is noise vs signal by repeating the same stimuli many times and measuring the response variation.
  3. Use the expressions for entropy and mutual information to derive an information rate.
       - Entropy = mathematical measure of uncertainty. In this context, how much uncertainty do I have about what you will do in the next second?
       - Mutual information = total entropy minus noise entropy. In this context, distinguishing actions that matter for the task from those that don't.


```
S_i = sifting number 
    = ratio of sensory information rate to behavioural throughput 
    = 10^9 / 10 = 10^8
```

- This may be the largest unexplained number in brain science.

- Human retina contain many millions of neurons, but they come in only 100 types.
- Cells of a given type and synaptic circuits between cells are distributed evenly across the retina. Therefore, modifying a single gene can alter synaptic circuitry in the same at many different sites within the visual field.
  - Convolutional neural networks use this property - all units within a layer share the same convolutional kernel and require learning only a few parameters.


- One human cone photoreceptor can transmit information at `270 bits/s`.
- One human eye has `6 million` cone photoreceptors = `6*10^6 * 270 bits/s = 162 * 10^7 bits/s  = 1.6 * 10^9 bits/s = 1.6 gigbits/s`.