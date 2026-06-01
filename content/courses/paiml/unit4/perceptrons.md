---
title: "Perceptrons"
date: 2026-06-01
description: "The perceptron model, representational power, the perceptron training rule, gradient descent, and the delta rule. Based on Mitchell Chapter 4, Section 4.4."
tags: ["paiml", "unit4", "perceptron", "delta-rule", "gradient-descent", "linear-classifier"]
categories: ["courses", "paiml"]
weight: 3
---

## Unit 4 Navigation

**← [Appropriate Problems for NN Learning](/courses/paiml/unit4/appropriate-problems/)**
&nbsp;|&nbsp;
**Next → [Multilayer Networks and Backpropagation](/courses/paiml/unit4/backpropagation/)**

---

## 4.4 Perceptrons

### What Is a Perceptron?

A **perceptron** is a single computational unit that takes a vector of real-valued inputs x₁, x₂, …, xₙ, computes their weighted sum, and outputs **+1** if the sum exceeds a threshold, **-1** otherwise.

```
Output o(x₁, ..., xₙ):
  = +1   if   w₀ + w₁x₁ + w₂x₂ + ... + wₙxₙ  >  0
  = -1   otherwise
```

Each wᵢ is a real-valued **weight**. The quantity **−w₀** is the **threshold** that the weighted sum must exceed.

Using a constant input x₀ = 1 (called the **bias input**), this simplifies to:

```
o(x) = sgn( w · x )
     = sgn( w₀x₀ + w₁x₁ + w₂x₂ + ... + wₙxₙ )
```

where **sgn** returns +1 for positive values and -1 for negative values.

```
Inputs         Weights        Aggregation    Output
  x₁ ─────── w₁ ─────┐
  x₂ ─────── w₂ ─────┤──→  Σ wᵢxᵢ  ──→  sgn(·)  ──→  +1 or -1
  x₃ ─────── w₃ ─────┘
  x₀=1 ───── w₀ (bias)
```

**Learning a perceptron** means choosing the weight vector **w = (w₀, w₁, …, wₙ)**.

---

## 4.4.1 Representational Power of Perceptrons

### The Decision Hyperplane

A perceptron represents a **hyperplane decision surface** in n-dimensional space. It outputs:
- **+1** for all instances on one side of the hyperplane `w · x = 0`
- **−1** for all instances on the other side

Sets of examples that can be correctly separated this way are called **linearly separable**.

### Boolean Functions a Perceptron Can Represent

| Function | Weights (example) | Notes |
|----------|------------------|-------|
| AND | w₀ = −0.8, w₁ = w₂ = 0.5 | Both inputs must be 1 |
| OR | w₀ = −0.3, w₁ = w₂ = 0.5 | At least one input must be 1 |
| NAND | Reverse signs of AND | |
| NOR | Reverse signs of OR | |
| m-of-n | All wᵢ = 0.5, threshold at m − 0.5 | At least m of n inputs true |

### The XOR Problem — Why a Single Perceptron Fails

XOR outputs 1 if and only if x₁ ≠ x₂:

```
x₂
 1 │  −    +
   │
 0 │  +    −
   └──────────── x₁
      0    1
```

The four points (0,0), (0,1), (1,0), (1,1) with labels (−1, +1, +1, −1) **cannot be separated by any straight line**. Therefore **no perceptron can correctly classify XOR**.

This limitation — shown by Minsky & Papert (1969) — led to the first "AI winter" for neural networks. Multilayer networks were later developed to overcome it.

### Two-Layer Networks Overcome This Limit

Every boolean function can be represented by a **two-layer network** of perceptrons:
- Express the function in Disjunctive Normal Form (OR of ANDs)
- First layer: compute each conjunction (AND of literals)
- Second layer: compute the disjunction (OR of conjunctions)

---

## 4.4.2 The Perceptron Training Rule

Start with random weights; iteratively update on each misclassified example:

```
Δwᵢ  =  η × (t − o) × xᵢ
wᵢ   ←  wᵢ + Δwᵢ
```

where:
- **t** = target output (+1 or −1)
- **o** = current perceptron output (+1 or −1)
- **η** (eta) = learning rate (small positive constant, e.g. 0.1)

### Algorithm

```
PERCEPTRON-TRAINING(training_examples, η):

  Initialize: w ← small random values
  Repeat until convergence:
    For each (x, t) in training_examples:
      o ← sgn(w · x)
      For each weight wᵢ:
        wᵢ ← wᵢ + η × (t − o) × xᵢ
```

### Why This Works

| Situation | (t − o) | Effect |
|-----------|---------|--------|
| Correctly classified | 0 | No weight change |
| Output −1, target +1 | +2 | Weights on active inputs increase → pushes sum positive |
| Output +1, target −1 | −2 | Weights on active inputs decrease → pushes sum negative |

### Convergence Guarantee

> **Perceptron Convergence Theorem:** If the training examples are linearly separable and the learning rate η is sufficiently small, the perceptron training rule converges to a correct weight vector in **finite steps**.

If the data are **not** linearly separable, the rule may cycle indefinitely. This is what motivates the delta rule.

---

## 4.4.3 Gradient Descent and the Delta Rule

### Motivation

The perceptron training rule fails for non-linearly separable data. The **delta rule** uses **gradient descent** to find the best-fit weight vector — even when perfect classification is impossible.

The delta rule is the direct foundation for the [Backpropagation algorithm](/courses/paiml/unit4/backpropagation/).

### Linear Units

Instead of the hard threshold, use a **linear unit** with output:

```
o(x) = w · x   (just the weighted sum, no threshold)
```

### The Error Surface

Define training error over all examples D:

```
E(w) = (1/2) × Σ (tᵈ − oᵈ)²
                d ∈ D
```

For a linear unit, this error surface is a **smooth bowl (paraboloid)** with a single global minimum. Gradient descent always finds it.

```
         E(w)
          │     ╱
          │    ╱  ← error surface (parabola in 2D)
          │   ╱
          │  ╱
          │ ╱ ← global minimum
          │╱___________________________ w
```

### Gradient Descent Update Rule

The gradient (slope) of E with respect to each weight wᵢ is:

```
∂E / ∂wᵢ  =  − Σ (tᵈ − oᵈ) × xᵢᵈ
               d ∈ D
```

Gradient descent moves in the direction of steepest descent (negative gradient):

```
Δwᵢ  =  −η × (∂E / ∂wᵢ)
      =   η × Σ (tᵈ − oᵈ) × xᵢᵈ
              d ∈ D
```

### Batch Gradient Descent Algorithm

```
GRADIENT-DESCENT(training_examples, η):

  Initialize: w ← small random values
  Repeat until convergence:
    Δwᵢ ← 0  for all i
    For each (x, t) in training_examples:
      o ← w · x                      ← linear unit output
      For each wᵢ:
        Δwᵢ ← Δwᵢ + η × (t − o) × xᵢ
    For each wᵢ:
      wᵢ ← wᵢ + Δwᵢ                 ← update after ALL examples seen
```

**Convergence:** Always reaches global minimum for linear units, given η small enough.

### Stochastic (Incremental) Gradient Descent

Update weights after **each individual example** instead of summing first:

```
For each (x, t) in training_examples:
  o ← w · x
  wᵢ ← wᵢ + η × (t − o) × xᵢ      ← immediate update per example
```

### Comparison: Batch vs. Stochastic

| Property | Batch | Stochastic |
|----------|-------|------------|
| Updates after | All examples | Each example |
| Follows true gradient | ✅ Yes | ✗ Approximation |
| Speed per update | Slower | Faster |
| Can escape local minima | Less likely | More likely |
| Used in practice | Less common | More common |

### The Delta Rule (LMS Rule)

The per-example update:

```
Δwᵢ  =  η × (t − o) × xᵢ
```

Also called: **LMS rule**, **Adaline rule**, **Widrow-Hoff rule**.

**Always converges** toward the minimum-error hypothesis, even when data is not linearly separable.

---

## 4.4.4 Comparing the Two Rules

| Property | Perceptron Training Rule | Delta Rule |
|----------|--------------------------|------------|
| Unit output | sgn(w · x) — thresholded | w · x — linear |
| Converges when | Data is linearly separable | Always |
| Converges to | Perfect classifier | Min-error approximation |
| Foundation for | — | Backpropagation |

Both rules use the same update formula `Δwᵢ = η(t − o)xᵢ`, but **o is defined differently**:
- Perceptron rule: `o = sgn(w · x)` → hard threshold
- Delta rule: `o = w · x` → no threshold

---

## Key Formulas Reference

| Expression | Meaning |
|-----------|---------|
| `o = sgn(w · x)` | Perceptron output |
| `E(w) = (1/2) Σ (t − o)²` | Squared error over training set |
| `Δwᵢ = η(t − o)xᵢ` | Perceptron / Delta rule weight update |
| `Δw = −η ∇E(w)` | Gradient descent general form |

---

## Practice Questions

1. Define a perceptron. What is the role of the weight w₀?
2. Show how a perceptron can represent the AND function. What weights would you choose?
3. Prove (or argue intuitively) that no single perceptron can represent XOR. Draw the input space.
4. What is the difference between the perceptron training rule and the delta rule? When does each converge?
5. Explain gradient descent using the error surface analogy. Why is the surface bowl-shaped for a linear unit?
6. Compare batch and stochastic gradient descent. When is stochastic preferred?

---

## References

- Mitchell, T.M. — *Machine Learning*, Chapter 4, Section 4.4 &nbsp; [📄 PDF](https://www.cim.mcgill.ca/~jer/courses/ai/readings/MitchellCh4.pdf)
- Minsky, M. & Papert, S. (1969) — *Perceptrons*
- Widrow, B. & Hoff, M.E. (1960) — *Adaptive Switching Circuits*

---

**← [Appropriate Problems for NN Learning](/courses/paiml/unit4/appropriate-problems/)**
&nbsp;|&nbsp;
**Next → [Multilayer Networks and Backpropagation](/courses/paiml/unit4/backpropagation/)**
