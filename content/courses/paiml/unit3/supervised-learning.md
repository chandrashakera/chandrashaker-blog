---
title: "3.2 Supervised Learning"
date: 2026-02-01
description: "Supervised learning concepts - VC dimension, PAC learning, SVM, kernel tricks and model generalization for M.Tech PAIML."
categories: ["Courses"]
tags: ["supervised-learning", "svm", "vc-dimension", "pac-learning", "kernel", "mtech"]
---

## Learning a Class from Examples

In supervised learning, we learn a **concept** (a class) from labeled examples.

### Key Concepts

**Hypothesis:** A candidate function mapping inputs to outputs.

**Hypothesis Space H:** All possible hypotheses a learner can consider.

**Version Space:** Subset of H consistent with all training examples.

```
Version Space = {h ∈ H | h is consistent with all training data}
```

### Candidate Elimination Algorithm

Maintains two boundaries:
- **G (General boundary):** Most general consistent hypotheses
- **S (Specific boundary):** Most specific consistent hypotheses

```
For each training example (x, label):
  If positive example:
    Remove from G any hypothesis inconsistent with x
    Generalize S to cover x (minimally)
  If negative example:
    Remove from S any hypothesis inconsistent with x
    Specialize G to exclude x (minimally)
```

---

## Vapnik-Chervonenkis (VC) Dimension

VC Dimension measures the **capacity** of a hypothesis space — how complex a model is.

### Definition

VC dimension of H = largest set of points that H can **shatter**.

**Shattering:** H shatters a set S if for every possible labeling of S, there exists a hypothesis in H consistent with that labeling.

### Examples

**Linear classifiers in 2D (lines):**
- Can shatter 3 points → VC dim = 3
- Cannot shatter 4 points (XOR problem) → VC dim = 3

```
3 points — all 8 labelings possible with a line:
○ ○     ● ○     ○ ●     ● ●     (etc.)
  ○       ○       ○       ○

4 points — XOR not linearly separable:
○ ●
● ○    ← No single line can separate these
```

### Why VC Dimension Matters

Higher VC dimension → more powerful model → more data needed to learn well.

**Sample complexity:** To learn with error ε and confidence δ:
```
m ≥ (1/ε)[ln|H| + ln(1/δ)]     (finite H)
m ≥ (1/ε)[VC(H) + ln(1/δ)]     (infinite H)
```

---

## Probably Approximately Correct (PAC) Learning

PAC learning asks: **How much data do we need to learn a good hypothesis?**

### PAC Definition

A concept class C is PAC-learnable if there exists an algorithm L such that for any:
- Target concept c ∈ C
- Distribution D over instances
- ε > 0 (error tolerance)
- δ > 0 (failure probability)

L outputs h with probability ≥ (1-δ) satisfying error(h) ≤ ε, using a **polynomial** number of samples.

### Sample Complexity for Finite H

```
m ≥ (1/ε)[ln|H| + ln(1/δ)]

Example:
  |H| = 1000 hypotheses
  ε = 0.1 (10% error tolerance)
  δ = 0.05 (5% failure probability)
  
  m ≥ 10 × [ln(1000) + ln(20)]
  m ≥ 10 × [6.9 + 3.0]
  m ≥ 99 examples
```

---

## Noise in Learning

Real data has noise — mislabeled examples, measurement errors.

### Handling Noise

**Statistical approach:** Allow some training errors, look for best-fit hypothesis.

**MDL approach:** Shorter hypothesis preferred even if it makes some errors.

**Cross-validation:** Use held-out data to detect overfitting.

---

## Learning Multiple Classes

**One-vs-All (OvA):** Train k binary classifiers for k classes.
```
Classifier 1: Class 1 vs {2,3,...,k}
Classifier 2: Class 2 vs {1,3,...,k}
...
Prediction: class with highest confidence
```

**One-vs-One (OvO):** Train k(k-1)/2 classifiers.
```
Classifier for each pair (i,j)
Prediction: majority vote
```

---

## Regression

Predicts a **continuous** output value.

### Linear Regression

```
ŷ = w₀ + w₁x₁ + w₂x₂ + ... + wₙxₙ = wᵀx

Loss function (MSE):
L(w) = (1/n) Σ (yi - ŷi)²

Gradient Descent Update:
w ← w - α × ∇L(w)
w ← w + (α/n) Σ (yi - ŷi) × xi
```

### Polynomial Regression

Extends linear regression with polynomial features:
```
ŷ = w₀ + w₁x + w₂x² + w₃x³ + ...
```

### Regularization

Prevents overfitting by penalizing large weights:

```
Ridge (L2): L(w) = MSE + λ Σwᵢ²
Lasso (L1): L(w) = MSE + λ Σ|wᵢ|
```

---

## Support Vector Machines (SVM)

SVM finds the **maximum margin hyperplane** that separates classes.

### Key Concepts

**Hyperplane:** w·x + b = 0

**Margin:** Distance between hyperplane and nearest points (support vectors).

**Support Vectors:** Data points closest to the hyperplane.

```
Maximize margin = 2/||w||
Subject to: yi(w·xi + b) ≥ 1 for all i
```

### Hard vs Soft Margin

**Hard margin SVM:** Requires perfect separation (no misclassification).

**Soft margin SVM:** Allows some misclassification using slack variables ξᵢ:
```
Minimize: (1/2)||w||² + C Σξᵢ
Subject to: yi(w·xi + b) ≥ 1 - ξᵢ,  ξᵢ ≥ 0

C = regularization parameter
High C → smaller margin, fewer errors
Low C → larger margin, more errors allowed
```

### Kernel Trick

For non-linearly separable data, map to higher dimension using kernel:

```
K(x, x') = φ(x)·φ(x')

Common Kernels:
  Linear:     K(x,x') = x·x'
  Polynomial: K(x,x') = (x·x' + 1)^d
  RBF/Gaussian: K(x,x') = exp(-γ||x-x'||²)
  Sigmoid:    K(x,x') = tanh(κx·x' - δ)
```

**Key insight:** We never need to compute φ(x) explicitly — just compute K(x,x').

### SVM Example

```
Data:          After RBF kernel transform:
○ ○ ● ●        ○ ○ | ● ●
○ ● ● ○   →    (linearly separable)
● ○ ○ ●

Linear SVM on transformed data finds optimal hyperplane.
```

---

## Model Selection and Generalization

### Cross-Validation

**k-fold Cross-Validation:**
```
1. Split data into k equal folds
2. For i = 1 to k:
   - Train on all folds except i
   - Test on fold i
3. Average performance across k folds
```

**Common:** k=5 or k=10.

### Generalization Bound

For hypothesis h with training error err_train and n samples:
```
err_test ≤ err_train + √(VC(H)×ln(n) + ln(1/δ)) / √n
```

As n → ∞, test error approaches training error.

---

## Dimensions of Supervised ML Algorithm

When designing a supervised ML algorithm, consider:

| Dimension | Options |
|-----------|---------|
| **Representation** | Decision trees, neural nets, SVM, linear models |
| **Evaluation** | Accuracy, MSE, likelihood, posterior |
| **Optimization** | Gradient descent, genetic algorithms, exact methods |

---

## Practice Questions

**Short Answer (2 marks each)**

1. What is VC dimension? Why is it important?
2. Define PAC learning. What does "probably approximately correct" mean?
3. What are support vectors in SVM?
4. What is the kernel trick? Give one example of a kernel function.

**Long Answer (8 marks each)**

1. Explain SVM with hard margin and soft margin. How does the regularization parameter C affect the model?
2. What is PAC learning? Derive the sample complexity for a finite hypothesis space.
3. Explain the kernel trick in SVM. Why is it computationally efficient? Compare RBF and polynomial kernels.

**Think & Apply**

1. For the following 2D dataset, identify the support vectors and describe the maximum margin hyperplane:
```
Positive: (1,1), (2,2), (3,1)
Negative: (1,3), (2,4), (3,3)
```

2. You have 10,000 training examples and your SVM with RBF kernel overfits. What changes would you make to C and γ? Why?

---

[← Intro to ML](/courses/paiml/unit3/intro-ml/) | [Next: Unit 4 →](/courses/paiml/unit4/)
