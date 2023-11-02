---
layout: post
date: 2023-11-01
title: "Podcast notes - AI Fundamentals: Benchmarks 101"
tags: podcast-notes ai
last_modified_at: 2023-11-03
status: budding
---

*These are notes from the podcast with some added external references.*

---

Hosts: swyx, Alessio Fanelli

Links:
- [Podcast on Latent Space](https://www.latent.space/p/benchmarks-101)

Synopsis: What does it really mean for an AI model to do well at X benchmark vs Y benchmark? How do you judge one model vs another?

---

### Traditional metrics

Three main measures for benchmark metrics:
  1. Accurancy = how many successful predictions the model does = `(TP + TN) / (TP + TN + FP + FN)`
  2. Precision = how many of them are good compared to the overall amount of predictions made = `TP / (TP + FP)`
  3. Recall = what proportion of positives were identified = `TP / (TP + FN)`

Translating to real-world application: 
  1. Precision: How many songs in a Spotify playlist did you like?
  2. Recall: Of all the Spotify songs that like, how many were put into the playlist?

Most benchmarks use F1 score = harmonic mean of precision and recoall = `2 * precision * recall / (precision + recall)`

### Recent metrics - especially for LLMs

[Stanford HELM](https://crfm.stanford.edu/2022/11/17/helm.html) - Rishi Bommasani, Percy Liang, Tony Lee
  - 7 metrics: accuracy, calibration, robustness, fairness, efficiency, general information bias, toxicity

### Benchmarking methodology

1. Zero-shot fashion: Do not provide any examples, just test how good the model is at generalizing.
2. Few shot: Provide `K` examples, see from there how good the model is.
3. Fine tune models: Take a bunch of data and fine-tune the model for a specific task and test it.