---
title: "5.1 Decision Trees"
date: 2026-02-01
sidebar: false
description: "Decision trees, ID3 algorithm, pruning, rule extraction, random forests and ensemble methods for M.Tech PAIML."
categories: ["Courses"]
tags: ["decision-trees", "id3", "random-forest", "ensemble", "boosting", "mtech"]
build:
  list: never
  render: always
---

## What are Decision Trees?

A decision tree is a hierarchical model that makes decisions by testing feature values, leading to a prediction at leaf nodes.

```
                 Outlook?
               /    |    \
           Sunny  Overcast  Rain
            |       |        |
         Humidity? YES    Wind?
          /    \          /    \
       High  Normal    Strong  Weak
        |       |        |      |
        NO     YES       NO    YES
```

**Advantages:**
- Easy to understand and interpret
- Handles both categorical and numerical features
- No feature scaling needed
- Can be visualized

## ID3 Algorithm

ID3 (Iterative Dichotomiser 3) builds decision trees using **Information Gain**.

### Entropy

Measures impurity/uncertainty in a dataset:

```
Entropy(S) = -Σ pᵢ × log₂(pᵢ)

where pᵢ = proportion of class i in S

Example: S has 9 positive, 5 negative
  p(+) = 9/14,  p(-) = 5/14
  
  Entropy(S) = -(9/14)log₂(9/14) - (5/14)log₂(5/14)
             = -(0.643)(−0.637) − (0.357)(−1.485)
             = 0.410 + 0.530 = 0.940
```

**Key values:**
- Entropy = 0 → perfectly pure (all same class)
- Entropy = 1 → maximum impurity (50-50 split for 2 classes)

### Information Gain

Reduction in entropy after splitting on attribute A:

```
Gain(S, A) = Entropy(S) - Σᵥ (|Sᵥ|/|S|) × Entropy(Sᵥ)

where Sᵥ = subset of S where A = v
```

### ID3 Algorithm

```
function ID3(S, Attributes):
  if all examples in S same class C:
    return Leaf(C)
  if Attributes is empty:
    return Leaf(majority class in S)
    
  A = attribute with highest Gain(S, A)
  Create node with test A
  
  for each value v of A:
    Sᵥ = {s ∈ S | A(s) = v}
    if Sᵥ is empty:
      add leaf with majority class of S
    else:
      add subtree ID3(Sᵥ, Attributes - {A})
  
  return tree
```

### Complete Example: Play Tennis

**Dataset:**

| Day | Outlook | Temp | Humidity | Wind | Play |
|-----|---------|------|----------|------|------|
| D1 | Sunny | Hot | High | Weak | No |
| D2 | Sunny | Hot | High | Strong | No |
| D3 | Overcast | Hot | High | Weak | Yes |
| D4 | Rain | Mild | High | Weak | Yes |
| D5 | Rain | Cool | Normal | Weak | Yes |
| D6 | Rain | Cool | Normal | Strong | No |
| D7 | Overcast | Cool | Normal | Strong | Yes |
| D8 | Sunny | Mild | High | Weak | No |
| D9 | Sunny | Cool | Normal | Weak | Yes |
| D10 | Rain | Mild | Normal | Weak | Yes |
| D11 | Sunny | Mild | Normal | Strong | Yes |
| D12 | Overcast | Mild | High | Strong | Yes |
| D13 | Overcast | Hot | Normal | Weak | Yes |
| D14 | Rain | Mild | High | Strong | No |

**Step 1:** Entropy(S) where 9 Yes, 5 No:
```
Entropy(S) = -(9/14)log₂(9/14) - (5/14)log₂(5/14) = 0.940
```

**Step 2:** Information Gain for Outlook:
```
S_Sunny = {D1,D2,D8,D9,D11} → 2 Yes, 3 No
Entropy(S_Sunny) = -(2/5)log₂(2/5) - (3/5)log₂(3/5) = 0.971

S_Overcast = {D3,D7,D12,D13} → 4 Yes, 0 No
Entropy(S_Overcast) = 0

S_Rain = {D4,D5,D6,D10,D14} → 3 Yes, 2 No
Entropy(S_Rain) = 0.971

Gain(S, Outlook) = 0.940 - (5/14×0.971 + 4/14×0 + 5/14×0.971)
                 = 0.940 - 0.693 = 0.247
```

**Calculate for all attributes:**
```
Gain(S, Temperature) = 0.029
Gain(S, Humidity) = 0.151
Gain(S, Wind) = 0.048
Gain(S, Outlook) = 0.247  ← HIGHEST → Root node
```

**Outlook = Overcast → Always Yes** (pure leaf)

**For Outlook = Sunny:** {D1,D2,D8,D9,D11}
```
Gain(S_Sunny, Humidity) = 0.971 (best) → Split on Humidity
  High → D1,D2,D8 → No (pure)
  Normal → D9,D11 → Yes (pure)
```

**Final Tree:**
```
Outlook?
├── Sunny → Humidity?
│          ├── High → NO
│          └── Normal → YES
├── Overcast → YES
└── Rain → Wind?
           ├── Strong → NO
           └── Weak → YES
```

## Types of Decision Trees

| Type | Target | Split Criterion |
|------|--------|----------------|
| **Classification Tree** | Discrete class | Information Gain, Gini |
| **Regression Tree** | Continuous value | Variance reduction |
| **Multivariate Tree** | Any | Linear combinations |

### Gini Impurity (used in CART)

```
Gini(S) = 1 - Σ pᵢ²

Example: 9 Yes, 5 No:
  Gini = 1 - (9/14)² - (5/14)² = 1 - 0.413 - 0.128 = 0.459
```

## Pruning

Pruning reduces overfitting by removing branches.

### Pre-Pruning (Early Stopping)

Stop growing tree when:
- Gain below threshold
- Too few examples in node
- Maximum depth reached

### Post-Pruning (Reduced Error Pruning)

```
1. Grow full tree
2. For each internal node (bottom-up):
   a. Compute accuracy with this node as leaf (majority class)
   b. Compute accuracy with subtree
   c. If accuracy with leaf ≥ accuracy with subtree:
      → Replace subtree with leaf
3. Repeat until no improvement
```

## Rule Extraction from Trees

Convert decision tree to IF-THEN rules:

**Each path from root to leaf = one rule**

```
From Tennis tree:

R1: IF Outlook=Sunny AND Humidity=High THEN Play=No
R2: IF Outlook=Sunny AND Humidity=Normal THEN Play=Yes
R3: IF Outlook=Overcast THEN Play=Yes
R4: IF Outlook=Rain AND Wind=Strong THEN Play=No
R5: IF Outlook=Rain AND Wind=Weak THEN Play=Yes
```

**Rule Post-Pruning:**
1. Convert tree to rules
2. For each rule, try removing conditions
3. Keep removal if accuracy improves on validation set
4. Sort rules by accuracy

## Multivariate Trees

Standard trees use one attribute per node (axis-aligned splits).

Multivariate trees use linear combinations:
```
w₁x₁ + w₂x₂ + ... + wₙxₙ > threshold → branch
```

More powerful but harder to interpret.

## Ensemble Methods

Combine multiple models for better performance.

### Bagging (Bootstrap Aggregating)

```
1. Create B bootstrap samples (sample with replacement)
2. Train one tree on each sample
3. Prediction: majority vote (classification) or average (regression)
```

**Reduces variance** — less overfitting than single tree.

### Random Forests

Extends bagging with feature randomness:

```
For each tree:
  1. Bootstrap sample
  2. At each split: choose best feature from RANDOM SUBSET of features
     (typically √p features for classification)
  3. Grow full tree (no pruning)

Final prediction: majority vote
```

**Advantages:**
- Very accurate
- Handles high dimensions well
- Gives feature importance

### Boosting

Trains models sequentially, each focusing on errors of previous:

**AdaBoost:**
```
1. Initialize equal weights for all examples
2. For t = 1 to T:
   a. Train weak learner hₜ on weighted data
   b. Compute weighted error εₜ
   c. αₜ = (1/2)ln((1-εₜ)/εₜ)
   d. Update weights:
      wᵢ ← wᵢ × exp(-αₜ × yᵢ × hₜ(xᵢ))
      Normalize weights
3. Final: H(x) = sign(Σ αₜhₜ(x))
```

**Gradient Boosting:**
```
Fit each new tree to residuals of previous ensemble
F_m(x) = F_{m-1}(x) + η × hₘ(x)
```

### Comparison

| Method | Bias | Variance | Interpretability |
|--------|------|----------|-----------------|
| Single tree | High | High | High |
| Bagging | Same | Lower | Low |
| Random Forest | Same | Much lower | Low |
| Boosting | Lower | Lower | Very low |

## Practice Questions

**Short Answer (2 marks each)**

1. What is entropy? What does entropy = 0 mean?
2. How is Information Gain calculated?
3. What is the difference between pre-pruning and post-pruning?
4. How does Random Forest differ from Bagging?

**Long Answer (8 marks each)**

1. Explain the ID3 algorithm. Apply it to build a decision tree for the tennis dataset (first 2 levels).
2. What is pruning in decision trees? Explain post-pruning with reduced error pruning.
3. Compare Bagging, Random Forests, and Boosting. Which would you use for a medical diagnosis problem and why?

**Think & Apply**

1. Calculate Information Gain for the following dataset when splitting on Weather:

| Weather | Traffic | Delay |
|---------|---------|-------|
| Rain | Heavy | Yes |
| Rain | Light | Yes |
| Sun | Heavy | No |
| Sun | Light | No |
| Cloud | Heavy | Yes |
| Cloud | Light | No |

2. A Random Forest has 100 trees. 60 predict "Yes", 40 predict "No". What is the final prediction? How does this reduce variance?

[← Unit 5 Overview](/courses/paiml/unit5/) | [Next: Reinforcement Learning →](/courses/paiml/unit5/reinforcement-learning/)
