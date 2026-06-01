---
title: "Recurrent Networks"
date: 2026-06-01
description: "Recurrent network architecture, training via unfolding in time, dynamic network structure — CASCADE-CORRELATION and pruning. Based on Mitchell Chapter 4, Section 4.8.3–4.8.4."
tags: ["paiml", "unit4", "recurrent-networks", "time-series", "bptt", "cascade-correlation", "rnn"]
categories: ["courses", "paiml"]
weight: 8
---

## Unit 4 Navigation

**← [Advanced Topics: Error Functions](/courses/paiml/unit4/advanced-error-functions/)**
&nbsp;|&nbsp;
**→ [Unit 5: Decision Trees & Reinforcement Learning](/courses/paiml/unit5/)**

---

## 4.8.3 Recurrent Networks

### Why Feedforward Networks Fall Short for Time Series

All networks discussed so far are **feedforward** — they map a fixed-size input to an output with **no memory of previous inputs**.

For time series problems, this is a fundamental limitation.

**Example:** Predict tomorrow's stock market index y(t+1) from today's economic indicators x(t).

```
Feedforward network:   x(t)  →  [Network]  →  y(t+1)
```

This uses only x(t). But if y(t+1) also depends on x(t−1), x(t−2), etc., the feedforward network has no access to that history.

**Partial fix:** Include multiple time steps as inputs:
```
x(t), x(t−1), x(t−2), ... as network inputs
```
But this requires deciding in advance how far back to look, and cannot handle **arbitrary-length dependencies**.

---

### The Recurrent Network Architecture

A **recurrent network** feeds the output of hidden units at time t back as additional inputs at time t+1 — creating a form of memory across time steps.

```
At time t:
┌──────────────────────────────────────────┐
│                                          │
│   Input:    x(t)  ──────────────┐        │
│   Context:  c(t) = b(t−1) ──┐  ↓        │
│                               ↓ [Unit b] │
│                              output b(t) │
│                                  ↓       │
│                             y(t+1)       │
│                                          │
│   b(t)  ────────────────→  c(t+1)        │
│         (feeds next step's context)      │
└──────────────────────────────────────────┘
```

**Key components:**

| Component | Description |
|-----------|-------------|
| Input unit x(t) | Current observation at time step t |
| Hidden unit b | Summarises all past inputs |
| Context unit c(t) | Receives value of b from previous step: c(t) = b(t−1) |
| Output y(t+1) | Prediction for the next time step |

**Why this captures history:**
b(t) depends on x(t) and c(t) = b(t−1).
b(t−1) depends on x(t−1) and b(t−2).
Recursively, b(t) depends on **all past inputs** x(t), x(t−1), x(t−2), … going back to the start of the sequence.

---

### Unfolding in Time — Training Recurrent Networks

Standard Backpropagation cannot handle cycles. The solution: **unfold** the recurrent network across T time steps, creating T copies of the feedforward network.

```
t−2:  x(t−2) + c(t−2)  →  [Copy 1]  →  y(t−1)
                                 ↓
                           b(t−2) → c(t−1)
                                 ↓
t−1:  x(t−1) + c(t−1)  →  [Copy 2]  →  y(t)
                                 ↓
                           b(t−1) → c(t)
                                 ↓
 t:   x(t) + c(t)       →  [Copy 3]  →  y(t+1)
```

The unfolded network has **no cycles** — it is a deep feedforward network. Standard Backpropagation (called **Backpropagation Through Time, BPTT**) can now be applied.

**Combining weights:** After training, the final recurrent weight w_ji is set to the **mean** of the corresponding weights across all copies.

---

### Multiple Recurrent Architectures

| Architecture | Memory Mechanism | Reference |
|---|---|---|
| Context unit model | Hidden unit output → input at next step | Mitchell (1997) |
| Jordan network | Output unit fed back as input | Jordan (1986) |
| Elman network | Hidden units copied to explicit context inputs | Elman (1990) |
| Fully recurrent | Every unit connects to every other across time | Various |
| LSTM | Memory cells with input / output / forget gates | Hochreiter & Schmidhuber (1997) |

---

### Practical Considerations

| Property | Details |
|----------|---------|
| Representational power | Greater than feedforward — models sequential dependencies of any length |
| Training difficulty | Harder than feedforward networks |
| Vanishing gradient problem | Gradients shrink exponentially over many time steps — hard to learn long-range patterns |
| Generalisation | Less reliable than feedforward networks |

**Vanishing gradient — intuition:**
In the unfolded network, gradients are multiplied by weights at each time step during backpropagation. If weights are small, gradients shrink exponentially as they travel back through time. Events far in the past become invisible to the learning algorithm.

**LSTM** (1997) solved this by introducing **memory cells** with explicit gating mechanisms that control information flow, maintaining gradient flow over long sequences.

---

### Connection to Modern AI

| Modern Architecture | Relation to Recurrent Networks |
|--------------------|---------------------------------|
| LSTM (1997) | Adds gates to control memory; standard for most sequence tasks until ~2017 |
| GRU (2014) | Simplified LSTM with fewer gates |
| Seq2Seq (2014) | Encoder–decoder using LSTMs; foundation of machine translation |
| Transformer (2017) | Replaces recurrence with attention mechanisms; basis of GPT, BERT |
| ChatGPT, Gemini | Transformer-based large language models |

---

## 4.8.4 Dynamically Modifying Network Structure

All methods so far keep the network architecture fixed — only weights change. Two approaches for **modifying structure during training**:

---

### Approach 1: Growing — CASCADE-CORRELATION (Fahlman & Lebiere, 1990)

**Philosophy:** Start minimal; grow only where needed.

```
ALGORITHM:

1. Start: no hidden units
          (inputs connected directly to outputs)

2. Train this minimal network

3. If error still too high:
   a. Create a new candidate hidden unit
   b. Train its input weights to MAXIMISE
      correlation with current residual error
   c. Install the unit; FREEZE its input weights
   d. Connect it to all output units
   e. Retrain OUTPUT weights only

4. Repeat from step 2 until error acceptable
```

**Network grows over time:**

```
Stage 0:   Input ──────────────────────────── Output

Stage 1:   Input ──→ h₁(frozen) ──→ Output
           Input ───────────────────────────→ Output

Stage 2:   Input ──→ h₁(frozen) ──→ Output
           Input ──→ h₂(frozen) ──→ Output
           Input ───────────────────────────→ Output
           h₁ ──────────────────────────────→ Output
```

Each new hidden unit receives inputs from all original inputs **and** all previously installed hidden units.

**Advantages:**
- Only one layer trained at a time → faster per phase
- Network grows only as needed — no manual architecture design

**Disadvantage:**
- Can overfit if allowed to grow too large
- Strong validation-based stopping required

---

### Approach 2: Pruning — Optimal Brain Damage (LeCun et al., 1990)

**Philosophy:** Start large; remove what is not needed.

```
ALGORITHM:

1. Train a full network to convergence

2. Compute SALIENCY of each weight:
   Saliency(w_ji) ≈ (second derivative of E w.r.t. w_ji) × w_ji²
   (How much does E increase if this weight is deleted?)

3. Remove the LEAST SALIENT connections

4. Retrain the pruned network

5. Repeat until performance degrades
```

**Saliency options:**
- Simple: remove near-zero weights (rough but fast)
- Better: use second-order information — "Optimal Brain Damage"

**Results on character recognition (LeCun et al.):**
- Weights reduced by a **factor of 4**
- **Slight improvement** in test accuracy (fewer parameters → less overfitting)
- **Significant improvement** in inference speed

---

### Growing vs. Pruning — Comparison

| Property | CASCADE-CORRELATION | Optimal Brain Damage |
|----------|--------------------|-----------------------|
| Starting point | Minimal network | Large network |
| Overfitting risk | High — can grow too large | Lower — removes parameters |
| Design effort | Low — grows automatically | Requires full training first |
| Final size | Unknown in advance | Controlled by pruning criterion |
| Use case | Architecture unknown | Good large network already exists |

---

## Unit 4 Complete Topic Summary

| Topic | Core Concept |
|-------|-------------|
| [Introduction](/courses/paiml/unit4/introduction/) | Biological motivation; ALVINN; network as hypothesis space |
| [Appropriate Problems](/courses/paiml/unit4/appropriate-problems/) | 6 characteristics; when to use ANNs |
| [Perceptrons](/courses/paiml/unit4/perceptrons/) | Linear classifier; XOR limit; perceptron rule; delta rule |
| [Multilayer Networks & Backpropagation](/courses/paiml/unit4/backpropagation/) | Sigmoid; forward/backward pass; δ values; weight update; momentum |
| [Remarks on Backpropagation](/courses/paiml/unit4/remarks-backpropagation/) | Local minima; universal approximator; hidden representations; overfitting |
| [Face Recognition Example](/courses/paiml/unit4/face-recognition/) | Design choices; 90% accuracy; what hidden units learn |
| [Advanced Error Functions](/courses/paiml/unit4/advanced-error-functions/) | Weight decay; cross-entropy; weight sharing; conjugate gradient |
| [Recurrent Networks](/courses/paiml/unit4/recurrent-networks/) | Time series; context units; BPTT; CASCADE-CORRELATION; pruning |

---

## Practice Questions

1. What is the key limitation of feedforward networks for time series? How do recurrent networks overcome it?
2. Explain "unfolding in time". Why does it allow standard Backpropagation to train recurrent networks?
3. What is the vanishing gradient problem? Why does it make learning long-range dependencies difficult?
4. Describe the CASCADE-CORRELATION algorithm. What does "maximising correlation with residual error" mean?
5. Compare weight removal by magnitude vs. by saliency (Optimal Brain Damage). Which is more principled and why?

---

## References

- Mitchell, T.M. — *Machine Learning*, Chapter 4, Sections 4.8.3–4.8.4 &nbsp; [📄 PDF](https://www.cim.mcgill.ca/~jer/courses/ai/readings/MitchellCh4.pdf)
- Jordan, M.I. (1986) — *Serial order: A parallel distributed processing approach*
- Elman, J.L. (1990) — *Finding structure in time*
- Fahlman, S.E. & Lebiere, C. (1990) — *The Cascade-Correlation Learning Architecture*
- LeCun, Y. et al. (1990) — *Optimal Brain Damage*
- Hochreiter, S. & Schmidhuber, J. (1997) — *Long Short-Term Memory*

---

**← [Advanced Topics: Error Functions](/courses/paiml/unit4/advanced-error-functions/)**
&nbsp;|&nbsp;
**→ [Unit 5: Decision Trees & Reinforcement Learning](/courses/paiml/unit5/)**  
**[PAIML Course Overview](/courses/paiml/)**
