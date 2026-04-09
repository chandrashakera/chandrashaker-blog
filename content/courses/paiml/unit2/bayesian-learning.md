---
title: "2.2 Bayesian Learning"
date: 2026-02-01
description: "Bayes theorem, concept learning, maximum likelihood, Naive Bayes classifier, Bayesian Belief Networks and EM algorithm for M.Tech PAIML."
categories: ["Courses"]
tags: ["bayesian", "naive-bayes", "bayes-theorem", "em-algorithm", "machine-learning", "mtech"]
_build:
  list: never
  render: always
---

## Bayes Theorem

Bayes theorem relates conditional probabilities:

```
P(h|D) = P(D|h) × P(h) / P(D)

where:
  P(h)   = Prior probability of hypothesis h
  P(D)   = Prior probability of data D
  P(D|h) = Likelihood — probability of D given h
  P(h|D) = Posterior — probability of h given D
```

### Example: Medical Diagnosis

```
P(Cancer) = 0.01        ← prior (1% of population)
P(+Test | Cancer) = 0.9 ← sensitivity
P(+Test | No Cancer) = 0.05 ← false positive rate

P(Cancer | +Test) = P(+Test|Cancer) × P(Cancer) / P(+Test)

P(+Test) = P(+Test|Cancer)×P(Cancer) + P(+Test|NoCancer)×P(NoCancer)
         = 0.9×0.01 + 0.05×0.99
         = 0.009 + 0.0495 = 0.0585

P(Cancer|+Test) = 0.9 × 0.01 / 0.0585 = 0.154 (15.4%)
```

## Maximum Likelihood Estimation (MLE)

Chooses the hypothesis h that maximizes P(D|h):

```
h_ML = argmax P(D|h)
         h
```

**Example:** For a coin with unknown bias θ:
- Data D: 3 heads, 2 tails
- P(D|θ) = θ³(1-θ)²
- MLE: dP/dθ = 0 → θ_ML = 3/5 = 0.6

## Minimum Description Length (MDL)

Choose the hypothesis that minimizes total description length:

```
h_MDL = argmin [L(h) + L(D|h)]
          h

where:
  L(h)   = length to describe hypothesis
  L(D|h) = length to describe data given hypothesis
```

MDL favors simpler hypotheses that explain data well (Occam's Razor).

## Bayes Optimal Classifier

Combines predictions from ALL hypotheses weighted by their probabilities:

```
P(vj|D) = Σ P(vj|hi) × P(hi|D)
           i

Prediction = argmax P(vj|D)
               vj
```

Most accurate but computationally expensive.

## Gibbs Algorithm

Practical approximation of Bayes optimal classifier:
1. Sample a hypothesis h from P(h|D)
2. Use h to classify new instance
3. Expected error ≤ 2 × Bayes optimal error

---
_build:
  list: never
  render: always
_build:
  list: never
  render: always

## Naive Bayes Classifier

Assumes features are conditionally independent given the class:

```
P(C|x1,x2,...,xn) ∝ P(C) × P(x1|C) × P(x2|C) × ... × P(xn|C)
```

### Algorithm

```
Training:
  For each class C:
    P(C) = count(C) / total_samples
    For each feature xi:
      P(xi|C) = count(xi,C) / count(C)

Prediction:
  For new instance x = (x1,...,xn):
    predict C* = argmax P(C) × Π P(xi|C)
                   C          i
```

### Example: Email Spam Classification

**Training Data:**

| Email | "offer" | "free" | "meeting" | Class |
|-------|---------|--------|-----------|-------|
| E1 | Yes | Yes | No | Spam |
| E2 | Yes | No | No | Spam |
| E3 | No | Yes | No | Spam |
| E4 | No | No | Yes | Ham |
| E5 | No | No | Yes | Ham |

**Probabilities:**
```
P(Spam) = 3/5 = 0.6,  P(Ham) = 2/5 = 0.4

P("offer"|Spam) = 2/3,  P("offer"|Ham) = 0/2 = 0
P("free"|Spam) = 2/3,   P("free"|Ham) = 0/2 = 0
P("meeting"|Spam) = 0/3, P("meeting"|Ham) = 2/2 = 1
```

**New email: "offer", "free", no "meeting"**
```
P(Spam|x) ∝ 0.6 × 2/3 × 2/3 × (1-0) = 0.267
P(Ham|x) ∝ 0.4 × 0 × 0 × (1-1) = 0

→ Classify as SPAM
```

**Note:** Use Laplace smoothing to handle zero probabilities.

## Bayesian Belief Networks

A Bayesian Belief Network (BBN) is a directed acyclic graph (DAG) where:
- **Nodes** represent random variables
- **Edges** represent conditional dependencies
- Each node has a Conditional Probability Table (CPT)

### Example: Alarm Network

```
Burglary  Earthquake
    \      /
     Alarm
    /     \
Phone    Radio
```

**CPT for Alarm:**

| Burglary | Earthquake | P(Alarm=T) |
|----------|------------|------------|
| T | T | 0.95 |
| T | F | 0.94 |
| F | T | 0.29 |
| F | F | 0.001 |

**Joint Probability:**
```
P(B,E,A,P,R) = P(B) × P(E) × P(A|B,E) × P(P|A) × P(R|E)
```

### Inference in BBN

Given evidence, compute probability of query variable:
```
P(Burglary | Alarm=True) = ?

Using Bayes theorem with summing out other variables.
```

## The EM Algorithm

Expectation-Maximization (EM) is used when data has missing/hidden variables.

### Two Steps

**E-step (Expectation):** Estimate missing values using current parameters:
```
Q(θ|θ_old) = E[log P(X,Z|θ) | X, θ_old]
```

**M-step (Maximization):** Update parameters to maximize expected log-likelihood:
```
θ_new = argmax Q(θ|θ_old)
           θ
```

### Example: Gaussian Mixture Model

```
Data: Points that came from 2 Gaussian distributions (unknown which)

E-step: P(zi=k | xi, θ) = P(xi|μk,σk) × P(k) / Σ P(xi|μj,σj)×P(j)

M-step: Update μk, σk, P(k) using weighted data points

Repeat until convergence.
```

## Practice Questions

**Short Answer (2 marks each)**

1. State Bayes theorem. Define each term.
2. What is the Naive Bayes assumption? When does it fail?
3. What is a Bayesian Belief Network? What does a node represent?
4. What are the two steps of the EM algorithm?

**Long Answer (8 marks each)**

1. Explain Naive Bayes classifier with a complete example. How do you handle zero probability using Laplace smoothing?
2. What is a Bayesian Belief Network? Explain with the Alarm example, including the joint probability calculation.
3. Explain the EM algorithm. How is it used for Gaussian Mixture Models?

**Think & Apply**

1. Given the following data, build a Naive Bayes classifier to predict whether to play tennis:

| Outlook | Temp | Humidity | Wind | Play |
|---------|------|----------|------|------|
| Sunny | Hot | High | Weak | No |
| Sunny | Hot | High | Strong | No |
| Overcast | Hot | High | Weak | Yes |
| Rain | Mild | High | Weak | Yes |
| Rain | Cool | Normal | Weak | Yes |

Predict: Outlook=Sunny, Temp=Cool, Humidity=High, Wind=Strong

[← Adversarial Search](/courses/paiml/unit2/adversarial-search/) | [Next: Unit 3 →](/courses/paiml/unit3/)
