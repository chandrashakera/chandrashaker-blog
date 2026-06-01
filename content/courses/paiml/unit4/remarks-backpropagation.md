---
title: "Remarks on the Backpropagation Algorithm"
date: 2026-06-01
description: "Convergence and local minima, representational power, inductive bias, hidden layer representations, and overfitting. Based on Mitchell Chapter 4, Section 4.6."
tags: ["paiml", "unit4", "backpropagation", "overfitting", "convergence", "local-minima"]
categories: ["courses", "paiml"]
weight: 5
---

## Unit 4 Navigation

**← [Multilayer Networks and Backpropagation](/courses/paiml/unit4/backpropagation/)**
&nbsp;|&nbsp;
**Next → [An Example: Face Recognition](/courses/paiml/unit4/face-recognition/)**

---

## 4.6.1 Convergence and Local Minima

### The Local Minima Problem

Unlike the linear unit — which has a single smooth bowl-shaped error surface — multilayer network error surfaces may have **many local minima**. Backpropagation is therefore only guaranteed to converge to **some local minimum**, not necessarily the global one.

```
    E(w)
     │         Local    Global
     │    Local Min     Min
     │    Max  ↓   \   /
     │   / \  / \  /\_/
     │  /   \/   \/
     └──────────────────── w
```

Despite this, Backpropagation works well in practice. Local minima are less severe than expected for two reasons:

**Reason 1 — High-dimensional escape routes:**
A network with many weights has an error surface in many dimensions. Being at a local minimum for one weight does not mean all weights are at a local minimum. More weights = more potential escape routes.

**Reason 2 — Near-zero initialisation:**
Weights start near zero, so the sigmoid is approximately linear early in training. Only later do weights grow into regions where complex nonlinear functions (and their associated local minima) emerge. By that time, gradient descent may already be near a good solution.

### Practical Strategies

| Strategy | Description |
|----------|-------------|
| Add momentum | Carries gradient descent through narrow local minima |
| Stochastic gradient descent | Different error surface per example; harder to get trapped |
| Multiple random restarts | Train several networks; keep the best result |
| Committee of networks | Average outputs of multiple trained networks |

---

## 4.6.2 Representational Power of Feedforward Networks

### Result 1 — Boolean Functions

> Any boolean function can be represented by a network with **two layers of units** (one hidden layer).

- Worst case: exponential number of hidden units required
- Constructive proof: one hidden unit per possible input vector

### Result 2 — Continuous Functions

> Every bounded continuous function can be approximated with **arbitrarily small error** by a network with one sigmoid hidden layer and a linear output layer.

*(Cybenko 1989; Hornik et al. 1989)*

### Result 3 — Arbitrary Functions

> Any function can be approximated to arbitrary accuracy by a network with **two sigmoid hidden layers** and a linear output layer.

*(Cybenko 1988)*

### Summary

| Function Class | Layers Needed | Notes |
|----------------|--------------|-------|
| Any boolean function | 2 (1 hidden) | Exponential units in worst case |
| Any bounded continuous | 2 (1 sigmoid + linear out) | Any accuracy |
| Any function | 3 (2 sigmoid + linear out) | Any accuracy |

**Practical implication:** In most applications, **1–2 hidden layers** are sufficient. ANNs are **universal function approximators**.

---

## 4.6.3 Inductive Bias

The hypothesis space of Backpropagation is the set of all possible weight vectors — a continuous n-dimensional space (n = number of weights). This continuous, differentiable structure is what makes gradient descent possible.

**Backpropagation's inductive bias:** roughly, **smooth interpolation between training data points**.

Given positive training examples with no negative examples between them, Backpropagation tends to classify intermediate points as positive — producing smoothly varying decision regions. This is well-suited to real-valued sensor data where nearby inputs should have similar outputs.

---

## 4.6.4 Hidden Layer Representations

One of the most striking properties of Backpropagation: **it discovers useful intermediate representations at hidden layers that were not defined by the designer**.

### The 8×3×8 Identity Network

**Task:** Learn the identity function — output the same 8-dimensional one-hot vector as the input.
**Architecture:** 8 inputs → **3 hidden units** → 8 outputs
**Constraint:** All 8 input patterns must pass through only 3 hidden units.

After 5000 training iterations, the hidden unit activations for each input are:

| Input pattern | Hidden activations (approx.) | Rounded |
|--------------|------------------------------|---------|
| 10000000 | 0.89, 0.04, 0.08 | 1, 0, 0 |
| 01000000 | 0.15, 0.99, 0.99 | 0, 1, 1 |
| 00100000 | 0.01, 0.97, 0.27 | 0, 1, 0 |
| 00010000 | 0.99, 0.97, 0.71 | 1, 1, 1 |
| 00001000 | 0.03, 0.05, 0.02 | 0, 0, 0 |
| 00000100 | 0.01, 0.11, 0.88 | 0, 0, 1 |
| 00000010 | 0.80, 0.01, 0.98 | 1, 0, 1 |
| 00000001 | 0.60, 0.94, 0.01 | 1, 1, 0 |

The rounded values are exactly the **standard 3-bit binary encoding** of integers 0–7.

The network **independently invented binary encoding** — without being told to. It was only given input-output pairs; it discovered on its own that a compact binary code is the most efficient hidden representation for 8 patterns using 3 units.

**Why this matters:** This self-organisation of internal representations is a key advantage of multilayer networks over methods requiring hand-crafted features.

---

## 4.6.5 Generalisation, Overfitting, and Stopping Criterion

### The Overfitting Problem

Minimising training error is a **poor stopping criterion**. Backpropagation can overfit — achieving very low training error but high error on unseen data.

**What happens during training:**

```
Error
  │
  │  \  Validation error — decreases then rises again
  │   \ /\
  │    \/  \──────────────────  ← overfitting region
  │         Training error (keeps falling)
  └──────────────────────────── Training iterations

        ↑
   Best stopping point = lowest validation error
```

**Early iterations:** Weights near zero → approximately linear, smooth function → good generalisation.

**Later iterations:** Weights grow → increasingly complex nonlinear function → starts fitting noise and idiosyncrasies specific to the training data.

### Cross-Validation Stopping (Recommended)

1. Split data into **training set** and **validation set** (never used for weight updates)
2. Run gradient descent on the training set
3. Every N iterations, evaluate error on the validation set
4. Keep a saved copy of weights at the **lowest validation error** seen so far
5. Stop when validation error has clearly risen above the saved best

Return the saved weights — not the final weights.

**k-fold cross-validation** for small datasets:
- Divide data into k equal subsets
- Run k experiments, each using a different subset as validation
- Average the optimal stopping iteration across all k runs
- Final training uses all data for that averaged number of iterations

### Weight Decay (Alternative)

Add a penalty term to the error function to discourage large weights:

```
E_new(w)  =  E_original(w)  +  γ × Σ w_ji²
```

This decays each weight by a small factor `(1 − 2γη)` per iteration, biasing the network toward simpler (lower-weight) solutions. See [Advanced Error Functions](/courses/paiml/unit4/advanced-error-functions/) for the full update rule.

---

## Summary of Key Remarks

| Aspect | Key Point |
|--------|-----------|
| Convergence | Local minimum only — not guaranteed global |
| Local minima in practice | Less severe than feared; high-dimensional networks have many escape routes |
| Expressiveness | Universal approximator: 1–2 hidden layers suffice for any function |
| Inductive bias | Smooth interpolation between training points |
| Hidden representations | Network invents its own internal features (e.g., binary encoding) |
| Overfitting risk | Serious; use cross-validation or weight decay |
| Stopping criterion | Use lowest validation error, not lowest training error |

---

## Practice Questions

1. Why are local minima less of a practical problem for large networks than for small ones?
2. What does "universal function approximator" mean? What are the limits of this claim?
3. Explain what happened in the 8×3×8 network experiment. Why is the discovered hidden representation significant?
4. Sketch a graph of training error and validation error vs. training iterations showing overfitting. Where is the optimal stopping point?
5. Compare cross-validation stopping vs. weight decay for avoiding overfitting. When would you prefer each?

---

## References

- Mitchell, T.M. — *Machine Learning*, Chapter 4, Section 4.6 &nbsp; [📄 PDF](https://www.cim.mcgill.ca/~jer/courses/ai/readings/MitchellCh4.pdf)
- Cybenko, G. (1989) — *Approximation by superpositions of a sigmoidal function*

---

**← [Multilayer Networks and Backpropagation](/courses/paiml/unit4/backpropagation/)**
&nbsp;|&nbsp;
**Next → [An Example: Face Recognition](/courses/paiml/unit4/face-recognition/)**
