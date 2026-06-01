---
title: "Introduction to Artificial Neural Networks"
date: 2026-06-01
description: "Biological motivation behind ANNs, neural network representations, and the ALVINN autonomous driving example. Based on Mitchell Chapter 4, Section 4.1–4.2."
tags: ["paiml", "unit4", "neural-networks", "introduction", "alvinn"]
categories: ["courses", "paiml"]
weight: 1
---

## Unit 4 Navigation

**← [Unit 4 Overview](/courses/paiml/unit4/)**
&nbsp;|&nbsp;
**Next → [Appropriate Problems for NN Learning](/courses/paiml/unit4/appropriate-problems/)**

---

## Overview

Artificial Neural Networks (ANNs) provide a **general, practical method for learning real-valued, discrete-valued, and vector-valued functions from examples**.

The Backpropagation algorithm — the cornerstone of ANN learning — uses gradient descent to tune network parameters to best fit a training set of input-output pairs.

### Why ANNs Matter

ANN learning has been proven effective in:
- Recognising handwritten characters (LeCun et al., 1989)
- Recognising spoken words (Lang et al., 1990)
- Recognising faces (Cottrell, 1990)
- Steering autonomous vehicles (Pomerleau, 1993)

---

## 4.1 Biological Motivation

The study of ANNs was inspired by the observation that **biological learning systems are built of densely interconnected neurons**.

### Key Facts from Neurobiology

| Fact | Value |
|------|-------|
| Neurons in human brain | ~10¹¹ |
| Average connections per neuron | ~10⁴ |
| Neuron switching time | ~10⁻³ seconds |
| Computer switching speed | ~10⁻¹⁰ seconds |
| Time to visually recognise your mother | ~0.1 seconds |

### The Parallel Processing Insight

In 0.1 seconds, with neurons switching at 10⁻³ seconds each, the brain can execute only about **100 sequential steps**. Yet visual recognition succeeds in that time. This means the brain must rely on **massively parallel computation** with information **distributed across many neurons**.

This observation motivated ANN designs where:
- Many simple units operate in parallel
- Representations are distributed (not stored in a single location)
- Learning modifies connection strengths between units

### Important Caveats

ANNs are only *loosely* inspired by biology. Differences include:
- ANN units output a single constant value; biological neurons output complex time-series of spikes
- ANN learning rules (like Backpropagation) are not known to operate in biological brains
- This course focuses on ANNs as **effective learning algorithms**, not as biological models

---

## 4.2 Neural Network Representations

### The ALVINN Example

**ALVINN** (Autonomous Land Vehicle In a Neural Network, Pomerleau 1993) is a landmark example of ANN learning in a real-world task.

**Task:** Steer an autonomous vehicle driving at normal highway speeds.

**Network architecture:**

```
┌──────────────────────────────────────────┐
│  30 Output Units (steering directions)   │
│  ↑  ↑  ↑  ...  ↑  ↑  ↑                 │
│  ┌─────────────────────────────┐         │
│  │    4 Hidden Units           │         │
│  └─────────────────────────────┘         │
│  ↑  ↑  ↑  ...  ↑  ↑  ↑                 │
│  30×32 Pixel Inputs (960 total)          │
│  [camera image from forward-facing lens] │
└──────────────────────────────────────────┘
```

| Component | Detail |
|-----------|--------|
| **Input** | 30×32 grid of pixel intensities from forward-facing camera = 960 inputs |
| **Hidden layer** | 4 units; each computes a weighted combination of all 960 inputs |
| **Output layer** | 30 units; each represents a steering direction |
| **Prediction** | The output unit with the highest value determines the steering command |

**Performance achieved:**
- Successfully drove at up to **70 miles per hour**
- Navigated **90 miles** on public highways (left lane of a divided highway, other vehicles present)
- Trained by mimicking a human driver for approximately 5 minutes

### What the Network Learns

The weights learned by ALVINN encode information about which pixel patterns correspond to which steering directions. For example:
- A road curving left activates hidden units that drive the output toward "steer left"
- A straight road ahead activates output units toward "straight ahead"

This is typical of how ANNs work: **the network structure defines the hypothesis space; learning finds the best weights within that space**.

### General Network Structure

ALVINN illustrates the structure common to most practical ANNs:
- Units arranged in **layers** forming a **directed acyclic graph**
- Units in each layer receive inputs from all units in the previous layer
- The network is a **fixed structure**; learning changes only the **weights on edges**

While ANNs can in general be cyclic or directed, the most practical and widely used networks (including Backpropagation networks) are **feedforward** (acyclic).

---

## Key Concepts from This Topic

- ANNs are motivated by the brain's ability to perform complex computation in very few sequential steps
- An ANN is a **graph of interconnected units**, each computing a weighted function of its inputs
- The **hypothesis space** is the set of all possible weight assignments to the network's edges
- Learning = finding the weight vector that minimises error on the training examples
- ANNs learn from **examples**, not from hand-coded rules

---

## Practice Questions

1. What biological observation motivates the parallel computation model in ANNs?
2. Describe the ALVINN system: its inputs, outputs, and what it learns.
3. What is the difference between the **network structure** and the **learned hypothesis** in an ANN?
4. Why are ANNs described as learning from "distributed representations"?

---

## References

- Mitchell, T.M. — *Machine Learning*, Chapter 4, Sections 4.1–4.2 &nbsp; [📄 PDF](https://www.cim.mcgill.ca/~jer/courses/ai/readings/MitchellCh4.pdf)
- Pomerleau, D.A. (1993) — *Knowledge-Based Training of Artificial Neural Networks for Autonomous Robot Driving*

---

**← [Unit 4 Overview](/courses/paiml/unit4/)**
&nbsp;|&nbsp;
**Next → [Appropriate Problems for NN Learning](/courses/paiml/unit4/appropriate-problems/)**
