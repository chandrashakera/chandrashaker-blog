---
title: "Advanced Topics of ANN: Alternative Error Functions"
date: 2026-06-01
description: "Weight decay, derivative-based errors, cross-entropy, weight sharing, and alternative optimisation methods. Based on Mitchell Chapter 4, Section 4.8.1–4.8.2."
tags: ["paiml", "unit4", "advanced-ann", "error-functions", "weight-decay", "cross-entropy", "weight-sharing"]
categories: ["courses", "paiml"]
weight: 7
---

## Unit 4 Navigation

**← [An Example: Face Recognition](/courses/paiml/unit4/face-recognition/)**
&nbsp;|&nbsp;
**Next → [Recurrent Networks](/courses/paiml/unit4/recurrent-networks/)**

---

## Why Modify the Error Function?

Standard Backpropagation minimises:

```
E(w) = (1/2) × Σ_d Σ_k  (t_kd − o_kd)²
```

This works for many cases. But we may also want to:
- **Reduce overfitting** by penalising large weights
- **Enforce invariance** by matching how the output varies with inputs
- **Output probabilities** rather than arbitrary real values
- **Enforce symmetry** across equivalent inputs

Each new objective leads to a **different error function E**, and hence a **different gradient descent update rule**.

> Gradient descent works for **any differentiable error function**. Change E → change what the network learns.

---

## 4.8.1 Alternative Error Functions

### A. Weight Decay (L2 Regularisation)

**Problem:** Large weights allow the network to fit noise in training data → overfitting.

**Solution:** Add a penalty for large weights to the error function:

```
E_new(w) = (1/2) × Σ_d Σ_k (t_kd − o_kd)²  +  γ × Σ_ji w_ji²
            ─────────────────────────────────     ──────────────
                    original squared error          weight penalty
```

The second term grows with weight magnitude. Minimising E_new requires trading off **fitting the data** against **keeping weights small**.

**Resulting weight update rule:**

```
w_ji  ←  w_ji × (1 − 2γη)  +  η × δ_j × x_ji
          ─────────────────    ─────────────────
          weight decays here   normal gradient step
```

Every weight is multiplied by `(1 − 2γη)` before the gradient step — it "decays" toward zero.

| γ value | Effect |
|---------|--------|
| γ = 0 | Standard Backpropagation (no regularisation) |
| Small γ | Mild preference for smaller weights |
| Large γ | Strong bias toward simple model |

**Choosing γ:** Use cross-validation. Too small: still overfits. Too large: underfits.

---

### B. Penalising Errors in Derivatives

**Motivation:** In some tasks we know not just what output values should be, but also **how the output should vary with input** — i.e., desired derivatives.

**Example — Translation-invariant character recognition:**
A digit '3' should be recognised whether it appears slightly to the left or right of centre in the image. The network's output should be nearly **invariant to small translations**. This means the derivative of the output with respect to horizontal position should be near zero.

**Extended error function:**

```
E = (1/2) Σ_d Σ_k (t_kd − o_kd)²
  + μ × Σ_d Σ_k Σ_j ( desired_deriv_kd_j − actual_deriv_kd_j )²
```

- First term: standard squared error on output values
- Second term: squared difference between desired and actual output derivatives
- **μ** controls the relative weight of the two objectives

**Applications:** Simard et al. (1992) — translation-invariant character recognition; Mitchell & Thrun (1993) — incorporating prior knowledge via derivatives.

---

### C. Cross-Entropy Error

**Motivation:** For binary classification, the network should output **probability estimates**, not just arbitrary real values. Squared error is not the best objective in this case.

**Example:** Predicting loan repayment — the target is 0 or 1 (did/didn't repay), but the true underlying function is a probability like 0.73.

**Cross-entropy error function:**

```
E = − Σ_d  [ t_d × log(o_d)  +  (1 − t_d) × log(1 − o_d) ]
```

where o_d is the network's probability estimate and t_d is the 0/1 target.

**Why cross-entropy is better than squared error for probabilities:**

| Property | Squared Error | Cross-Entropy |
|----------|--------------|---------------|
| Assumes output represents | A value | A probability |
| Gradient when confidently wrong | Small (saturated sigmoid) | Large |
| Maximum likelihood estimator | No | Yes (for Bernoulli targets) |

Cross-entropy gives a **stronger learning signal** when the network is confidently wrong — it avoids the "vanishing gradient at saturation" problem that squared error has with sigmoid outputs.

---

### D. Weight Sharing

**Motivation:** Some inputs should be treated **equivalently** — we want the network to enforce this symmetry automatically.

**Example — Time-Delay Neural Network (TDNN) for Speech Recognition:**
- Input: speech frequency components at 12 consecutive time windows (144ms total)
- Physical fact: the features that identify the sound "eee" should be **the same regardless of which time window** the sound appears in — time-invariance
- Solution: force all units processing different time windows to **share identical weights**

```
Time windows:   t₁    t₂    t₃    ...    t₁₂
                ↓     ↓     ↓           ↓
              [Unit] [Unit] [Unit]...[Unit]
                ↑─────↑─────↑──────────↑
                All share identical weights
```

**Implementation:**
1. Compute gradient update for the shared weight independently within each unit
2. Replace all instances with their **mean value**
3. Repeat — the shared weights now minimise a modified E that enforces the symmetry

**Why this helps:**
- Fewer free parameters → less overfitting
- Encodes known problem structure explicitly
- Better generalisation to unseen inputs

**Modern relevance:** This is the direct theoretical foundation of **Convolutional Neural Networks (CNNs)** — the standard architecture for image recognition. In CNNs, the same filter weights apply at every spatial position (translation equivariance).

---

## 4.8.2 Alternative Optimisation Methods

Standard gradient descent uses a **fixed step size** η. The following methods choose the step size (and sometimes direction) more adaptively.

### Line Search

After choosing a descent direction, find the **optimal step size** along that line:

```
α* = argmin  E( w − α × ∇E(w) )
      α
```

Each step moves exactly to the minimum along the chosen direction — allowing much larger or smaller steps than a fixed η.

### Conjugate Gradient Method

Combines line search with a smarter **choice of search direction**:

1. **Step 1:** Move in the steepest descent direction (negative gradient)
2. **Step 2:** Choose the next direction so that it does not undo progress from the previous step — the previously-zeroed gradient component **stays zero**

```
Standard gradient descent:       Conjugate gradient:
  zig-zags toward minimum          more direct path, less backtracking
  many small steps                 n steps for n-dimensional quadratic
```

**Convergence:** For a quadratic (bowl-shaped) error surface in n dimensions, conjugate gradient converges in exactly **n steps** — vs. potentially thousands for fixed-rate gradient descent.

**In practice for ANNs:**
- Trains faster (fewer iterations needed)
- Does **not** significantly improve final generalisation accuracy
- May converge to different local minima than standard gradient descent

---

## Comparison of Error Functions

| Error Function | Use Case | Modern Name |
|----------------|----------|-------------|
| Squared error | General regression | MSE — Mean Squared Error |
| Squared error + weight penalty | Reduce overfitting | L2 regularisation |
| Squared error + derivative penalty | Enforce invariance | Tangent propagation |
| Cross-entropy | Binary / multiclass classification | Binary cross-entropy |
| Weight sharing | Symmetric inputs (time, space) | Convolutional layers in CNNs |

---

## Key Formulas Reference

| Expression | Meaning |
|-----------|---------|
| `E = (1/2)Σ(t−o)² + γΣw²` | Weight decay error function |
| `w_ji ← w_ji(1−2γη) + ηδ_jx_ji` | Weight decay update rule |
| `E = −Σ[t·log(o) + (1−t)·log(1−o)]` | Cross-entropy error |
| Shared weight = mean of per-unit gradients | Weight sharing update |

---

## Practice Questions

1. Derive the weight update rule for gradient descent with weight decay. Show that each weight is multiplied by `(1 − 2γη)` per iteration.
2. Why is cross-entropy better than squared error when network outputs should be probabilities?
3. What is weight sharing? Describe a task where it is appropriate and explain the symmetry it enforces.
4. Explain the conjugate gradient method. How does it differ from steepest descent, and why does it converge faster?
5. If your network is overfitting, what error function modification would you apply? What hyperparameter must be tuned and how?

---

## References

- Mitchell, T.M. — *Machine Learning*, Chapter 4, Section 4.8.1–4.8.2 &nbsp; [📄 PDF](https://www.cim.mcgill.ca/~jer/courses/ai/readings/MitchellCh4.pdf)
- Simard, P. et al. (1992) — *Efficient pattern recognition using a new transformation distance*
- Waibel, A. et al. (1989) — *Phoneme recognition using time-delay neural networks*

---

**← [An Example: Face Recognition](/courses/paiml/unit4/face-recognition/)**
&nbsp;|&nbsp;
**Next → [Recurrent Networks](/courses/paiml/unit4/recurrent-networks/)**
