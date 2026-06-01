---
title: "Multilayer Networks and Backpropagation Algorithm"
date: 2026-06-01
description: "Sigmoid units, the Backpropagation algorithm step-by-step, momentum, and the derivation of weight-update rules. Based on Mitchell Chapter 4, Section 4.5."
tags: ["paiml", "unit4", "backpropagation", "sigmoid", "multilayer-network", "gradient-descent"]
categories: ["courses", "paiml"]
weight: 4
---

## Unit 4 Navigation

**← [Perceptrons](/courses/paiml/unit4/perceptrons/)**
&nbsp;|&nbsp;
**Next → [Remarks on Backpropagation](/courses/paiml/unit4/remarks-backpropagation/)**

---

## Why Multilayer Networks?

The [perceptron](/courses/paiml/unit4/perceptrons/) can only represent **linear decision surfaces**. Real-world problems like vowel recognition or face direction require **nonlinear** boundaries.

Multilayer networks trained with Backpropagation learn **rich nonlinear decision surfaces** — curved, irregular boundaries that no single perceptron could produce.

---

## 4.5.1 The Sigmoid Unit

### The Problem with Perceptrons in Multilayer Networks

We need units that are:
1. **Nonlinear** — to express complex functions
2. **Differentiable everywhere** — to apply gradient descent

Perceptrons fail condition 2 (hard threshold is not differentiable at the boundary). Linear units fail condition 1 (stacking linear units still gives a linear function).

### The Sigmoid (Logistic) Function

The **sigmoid unit** is a smooth, differentiable approximation to the hard threshold:

```
net  =  w₀x₀ + w₁x₁ + w₂x₂ + ... + wₙxₙ   (weighted sum)

         1
o  =  ─────────                               (sigmoid output)
       1 + e^(−net)
```

```
σ(net)
 1.0 │               ─────────────
     │          ────╱
 0.5 │    ─────╱
     │───╱
 0.0 └─────────────────────────────── net
         negative    0    positive
```

**Key properties:**

| Property | Value |
|----------|-------|
| Output range | (0, 1) — always between 0 and 1 |
| Large positive input | Output approaches 1 |
| Large negative input | Output approaches 0 |
| Derivative | σ(net) × (1 − σ(net)) — computable from output value! |

The derivative being expressible purely from the output value is crucial for efficient Backpropagation.

---

## 4.5.2 The Backpropagation Algorithm

Backpropagation learns weights for a multilayer network using gradient descent to minimise total squared error across all training examples and all output units:

```
E(w) = (1/2) × Σ  Σ  (t_kd − o_kd)²
                d  k
```

where d ranges over training examples and k ranges over output units.

### Network Notation

```
        Output units:  o_k  (target: t_k)
              ↑    ↑    ↑
         weights: w_kh
              ↑    ↑    ↑
        Hidden units:  o_h
              ↑    ↑    ↑
         weights: w_hi
              ↑    ↑    ↑
        Input units:   x_i
```

- **x_ji** = input from node i to unit j
- **w_ji** = weight on that connection
- **δ_j** (delta) = error term for unit j

### Full Algorithm

```
BACKPROPAGATION(training_examples, η, n_in, n_hidden, n_out):

  1. Create network: n_in inputs → n_hidden hidden → n_out outputs
  2. Initialise all weights to small random values in (−0.05, 0.05)

  3. Until stopping condition:
     For each training example (x, t):

     ── FORWARD PASS ──────────────────────────────────────────
     a. Feed x into network; compute output o_u for every unit u

     ── BACKWARD PASS ──────────────────────────────────────────
     b. For each OUTPUT unit k:
           δ_k  ←  o_k × (1 − o_k) × (t_k − o_k)

     c. For each HIDDEN unit h (working back from output layer):
           δ_h  ←  o_h × (1 − o_h) × Σ (w_kh × δ_k)
                                       k

     ── WEIGHT UPDATE ──────────────────────────────────────────
     d. For every weight w_ji:
           w_ji  ←  w_ji + Δw_ji
           where  Δw_ji = η × δ_j × x_ji
```

### Understanding Each Step

**Step (a) — Forward pass:**

For each unit j, compute:
```
net_j  =  Σ  w_ji × x_ji        (weighted sum of inputs)
           i

o_j    =  1 / (1 + e^(−net_j))  (sigmoid of weighted sum)
```

**Step (b) — Output unit error term δ_k:**

```
δ_k  =  o_k × (1 − o_k) × (t_k − o_k)
         ────────────────   ──────────
         sigmoid derivative  prediction error
```

The term `(t_k − o_k)` is the raw error. Multiplying by `o_k(1 − o_k)` (the sigmoid derivative) correctly accounts for the nonlinear activation.

**Step (c) — Hidden unit error term δ_h:**

Hidden units have no direct target value. Their error is back-propagated from the output layer:

```
δ_h  =  o_h × (1 − o_h) × Σ (w_kh × δ_k)
                             k
```

The weight `w_kh` determines how much hidden unit h is "responsible for" the error in output unit k. This is the core idea that gives Backpropagation its name.

**Step (d) — Weight update:**

```
Δw_ji  =  η × δ_j × x_ji
```

The weight change is proportional to:
- **η** — learning rate
- **δ_j** — how much unit j's activation needs to change
- **x_ji** — strength of the input signal from unit i

### Information Flow Summary

```
FORWARD PASS:   inputs ──→ hidden ──→ outputs    (compute o values)
BACKWARD PASS:  outputs ──→ hidden              (compute δ values)
UPDATE:         all weights adjusted using δ_j × x_ji
```

---

## Generalising to Deeper Networks

For networks of any depth, the hidden unit rule generalises to:

```
δ_r  =  o_r × (1 − o_r) × Σ  w_sr × δ_s
                             s ∈ Downstream(r)
```

where Downstream(r) = all units that directly receive input from r. This works for any directed acyclic graph, not just uniform layered networks.

---

## 4.5.3 Adding Momentum

A common improvement to avoid slow convergence and help escape narrow local minima:

```
Δw_ji(n)  =  η × δ_j × x_ji  +  α × Δw_ji(n−1)
              ───────────────     ─────────────────
              current gradient    previous update × momentum
```

where:
- **n** = current training iteration
- **α** (alpha) = momentum constant, 0 ≤ α < 1

**Analogy:** A ball rolling down the error surface. Without momentum it stops at every flat spot. With momentum it keeps rolling — crossing small flat regions and narrow local minima.

**Effect:**
- Accelerates learning when gradient consistently points the same way
- Can carry the search through shallow local minima
- Increases effective step size on flat parts of the error surface

---

## 4.5.4 Derivation of the Update Rule

*(Optional — for deeper understanding)*

The update rule comes from applying the chain rule to `∂E_d / ∂w_ji`:

```
∂E_d / ∂w_ji  =  (∂E_d / ∂net_j) × (∂net_j / ∂w_ji)
               =  (∂E_d / ∂net_j) × x_ji
```

For **output unit k**:
```
∂E_d / ∂net_k  =  −(t_k − o_k) × o_k × (1 − o_k)  =  −δ_k
```

For **hidden unit h** (error flows through all downstream units):
```
∂E_d / ∂net_h  =  −o_h(1−o_h) × Σ w_kh × δ_k  =  −δ_h
                                   k
```

Substituting back:
```
Δw_ji  =  −η × (−δ_j) × x_ji  =  η × δ_j × x_ji
```

**Same formula for both output and hidden units.** Only the definition of δ_j differs.

---

## Worked Example

Network: 2 inputs → 1 hidden unit → 1 output unit  
Given: x₁ = 0.5, x₂ = 0.3, target t = 0.9, η = 0.5  
Weights: w_h0 = 0.1, w_h1 = 0.4, w_h2 = 0.2, w_k0 = −0.1, w_kh = 0.6

**Forward pass:**
```
net_h  =  0.1 + 0.4(0.5) + 0.2(0.3)  =  0.36
o_h    =  1 / (1 + e^−0.36)           ≈  0.589

net_k  =  −0.1 + 0.6(0.589)           =  0.253
o_k    =  1 / (1 + e^−0.253)          ≈  0.563
```

**Backward pass:**
```
δ_k  =  0.563 × (1 − 0.563) × (0.9 − 0.563)  ≈  0.083
δ_h  =  0.589 × (1 − 0.589) × (0.6 × 0.083)  ≈  0.012
```

**Weight updates:**
```
Δw_kh  =  0.5 × 0.083 × 0.589  ≈  0.024
Δw_h1  =  0.5 × 0.012 × 0.5    ≈  0.003
```

---

## Key Formulas Reference

| Expression | Meaning |
|-----------|---------|
| `o = 1 / (1 + e^(−net))` | Sigmoid activation |
| `σ'(net) = o × (1 − o)` | Sigmoid derivative |
| `E(w) = (1/2) Σ_d Σ_k (t_kd − o_kd)²` | Total squared error |
| `δ_k = o_k(1−o_k)(t_k − o_k)` | Output unit delta |
| `δ_h = o_h(1−o_h) Σ_k w_kh δ_k` | Hidden unit delta |
| `Δw_ji = η δ_j x_ji` | Weight update |
| `Δw_ji(n) = η δ_j x_ji + α Δw_ji(n−1)` | With momentum |

---

## Practice Questions

1. Why can't we build useful multilayer networks using only linear units? What does the sigmoid solve?
2. Trace the forward and backward passes for the worked example above with different initial weights.
3. What is the role of δ_j in the weight update? How does it differ for output vs. hidden units?
4. Why is momentum added? What problem does it solve?
5. Explain in words why the hidden unit delta must sum over all downstream units.

---

## References

- Mitchell, T.M. — *Machine Learning*, Chapter 4, Section 4.5 &nbsp; [📄 PDF](https://www.cim.mcgill.ca/~jer/courses/ai/readings/MitchellCh4.pdf)
- Rumelhart, D.E., Hinton, G.E. & Williams, R.J. (1986) — *Learning representations by back-propagating errors*

---

**← [Perceptrons](/courses/paiml/unit4/perceptrons/)**
&nbsp;|&nbsp;
**Next → [Remarks on Backpropagation](/courses/paiml/unit4/remarks-backpropagation/)**
