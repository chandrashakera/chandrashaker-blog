---
title: "3.1 Introduction to Machine Learning"
date: 2026-02-01
description: "Machine learning applications, types of learning - classification, regression, unsupervised and reinforcement learning for M.Tech PAIML."
categories: ["Courses"]
tags: ["machine-learning", "classification", "regression", "unsupervised", "reinforcement", "mtech"]
build:
  list: never
  render: always
---

## What is Machine Learning?

Machine Learning (ML) is a subset of AI that enables systems to **learn from data** and improve performance without being explicitly programmed.

**Tom Mitchell's Definition:**
> "A computer program is said to learn from experience E with respect to some task T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E."

### Example — Email Spam Filter
- **Task T:** Classify emails as spam or not spam
- **Experience E:** Training emails labeled spam/not spam
- **Performance P:** Accuracy of classification

## Examples of Machine Learning Applications

| Domain | Application | Type of ML |
|--------|-------------|------------|
| Healthcare | Disease diagnosis | Classification |
| Finance | Stock price prediction | Regression |
| E-commerce | Product recommendations | Unsupervised |
| Gaming | Game playing agents | Reinforcement |
| NLP | Language translation | Supervised |
| Security | Fraud detection | Classification |
| Robotics | Robot navigation | Reinforcement |
| Computer Vision | Face recognition | Classification |

## Types of Machine Learning

### 1. Supervised Learning

Learns from **labeled training data** — each example has input + correct output.

```
Training: (x1,y1), (x2,y2), ..., (xn,yn)
Goal: Learn function f: X → Y
Test: Predict y for new x
```

**Sub-types:**
- **Classification:** Output is discrete (spam/not spam, cat/dog)
- **Regression:** Output is continuous (house price, temperature)

**Algorithms:** Decision Trees, SVM, Neural Networks, Naive Bayes

### 2. Unsupervised Learning

Learns from **unlabeled data** — finds hidden patterns or structure.

```
Training: x1, x2, ..., xn (no labels)
Goal: Discover structure in data
```

**Sub-types:**
- **Clustering:** Group similar data points (K-means)
- **Dimensionality Reduction:** Reduce features (PCA)
- **Association:** Find rules (market basket analysis)

**Example:** Customer segmentation — group customers by buying behavior without predefined categories.

### 3. Semi-supervised Learning

Uses a **small amount of labeled data** + large amount of unlabeled data.

**Why useful:** Labeling data is expensive. Getting raw data is cheap.

**Example:** Google Photos — few labeled photos + many unlabeled photos to learn face recognition.

### 4. Reinforcement Learning

Agent learns by **interacting with environment** — receives rewards/penalties.

```
Agent → Action → Environment → State + Reward → Agent
```

**Key elements:**
- **Agent:** Learner/decision maker
- **Environment:** What agent interacts with
- **State:** Current situation
- **Action:** What agent does
- **Reward:** Feedback signal
- **Policy:** Agent's strategy

**Example:** AlphaGo — learns to play Go by playing millions of games, receiving +reward for winning, -reward for losing.

### 5. Learning Associations

Find rules describing associations between variables.

**Example — Market Basket Analysis:**
```
{bread, butter} → {milk}    support=30%, confidence=70%

"70% of customers who buy bread and butter also buy milk"
```

**Apriori Algorithm** is commonly used for association rule mining.

## The Machine Learning Pipeline

```
1. Data Collection
        ↓
2. Data Preprocessing
   (cleaning, normalization, feature selection)
        ↓
3. Model Selection
        ↓
4. Training
        ↓
5. Evaluation
        ↓
6. Deployment
        ↓
7. Monitoring & Updating
```

## Key Concepts

### Overfitting vs Underfitting

```
Underfitting: Model too simple → high training error, high test error
              (High Bias)

Good fit:     Low training error, low test error

Overfitting:  Model too complex → low training error, high test error
              (High Variance)
```

### Bias-Variance Tradeoff

```
Total Error = Bias² + Variance + Irreducible Noise

High Bias (Underfitting): Doesn't capture data patterns
High Variance (Overfitting): Memorizes training data, poor generalization
```

### Training, Validation, Test Split

| Set | Purpose | Typical Size |
|-----|---------|-------------|
| Training | Fit model parameters | 60-70% |
| Validation | Tune hyperparameters | 10-20% |
| Test | Final evaluation | 20-30% |

## Performance Metrics

### Classification Metrics

**Confusion Matrix:**
```
                 Predicted
                 Pos    Neg
Actual   Pos   [TP]   [FN]
         Neg   [FP]   [TN]
```

| Metric | Formula |
|--------|---------|
| Accuracy | (TP+TN)/(TP+TN+FP+FN) |
| Precision | TP/(TP+FP) |
| Recall | TP/(TP+FN) |
| F1-Score | 2×(Precision×Recall)/(Precision+Recall) |

### Regression Metrics

| Metric | Formula | Meaning |
|--------|---------|---------|
| MAE | Σ\|y-ŷ\|/n | Average absolute error |
| MSE | Σ(y-ŷ)²/n | Penalizes large errors |
| RMSE | √MSE | Same units as y |
| R² | 1 - SS_res/SS_tot | Variance explained (0-1) |

## Practice Questions

**Short Answer (2 marks each)**

1. Define machine learning. Give Mitchell's formal definition.
2. What is the difference between supervised and unsupervised learning?
3. Define overfitting and underfitting.
4. What is the bias-variance tradeoff?

**Long Answer (8 marks each)**

1. Explain the four types of machine learning with examples and algorithms for each.
2. What is the machine learning pipeline? Explain each step with an example.
3. Explain the performance metrics for classification. What is a confusion matrix?

**Think & Apply**

1. For each scenario, identify the type of ML and appropriate algorithm:
   - Predicting house prices from features
   - Grouping news articles by topic
   - Teaching a robot to walk
   - Detecting credit card fraud

2. A spam filter has: TP=90, FP=10, FN=5, TN=895. Calculate accuracy, precision, recall and F1-score. Which metric is most important for a spam filter?

[← Unit 3 Overview](/courses/paiml/unit3/) | [Next: Supervised Learning →](/courses/paiml/unit3/supervised-learning/)
