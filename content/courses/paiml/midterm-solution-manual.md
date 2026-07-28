---
title: "PAIML I Mid-Term Examination — Solution Manual"
date: 2026-04-25
description: "Complete solutions for PAIML I Mid-Term exam — Part A MCQ/FIB answers and Part B detailed solutions covering AI agents, search, adversarial search, Bayesian learning and regression."
categories: ["Courses"]
tags: ["ai", "machine-learning", "mtech", "exam", "solutions"]
sidebar: false
build:
  list: never
  render: always
---

> Complete solutions for I Mid-Term Examination. Part A: 10M | Part B: 4×5=20M | Total: 30M

---

## Part A Solutions (1 × 10 = 10 M)

| Q | Question | Answer |
|---|----------|--------|
| **a** | FIB: An AI agent that selects actions using only the current percept is called a ___ agent | **Simple Reflex** |
| **b** | MCQ: Which uninformed search is guaranteed to find the shallowest solution? | **(B) Breadth First Search (BFS)** |
| **c** | FIB: For A\* to guarantee an optimal solution, h(n) must be ___ | **Admissible (h(n) ≤ h\*(n))** |
| **d** | MCQ: The value at a MAX node in Minimax is: | **(B) The maximum of its child values** |
| **e** | FIB: Alpha-Beta pruning prunes subtrees that cannot affect the final ___ value | **Minimax (optimal)** |
| **f** | MCQ: Naïve Bayes is 'naïve' because it assumes features are: | **(B) Conditionally independent given the class label** |
| **g** | FIB: P(h) in Bayes' Theorem is called the ___ probability | **Prior** |
| **h** | MCQ: Which is NOT typically modelled as a CSP? | **(D) Finding the shortest path in a weighted graph** |
| **i** | FIB: Learning by interacting with an environment via rewards/penalties is called ___ Learning | **Reinforcement** |
| **j** | MCQ: 'Learning' in ML best means: | **(B) Improving task performance through past experience and data** |

---

## Part B Solutions

---

### Q.2(a) — Define AI. Short note on goal-based agent with diagram. [2M]

**Definition of Artificial Intelligence**

Artificial Intelligence (AI) is the science and engineering of making intelligent machines, especially intelligent computer programs. It involves designing systems that perceive their environment and take actions that maximize their chance of achieving goals. (Russell & Norvig: 'AI is the study of agents that receive percepts from the environment and perform actions.')

**Goal-Based Agent**

A goal-based agent extends the model-based reflex agent by incorporating goal information. Instead of using condition-action rules, it evaluates which action will bring it closer to its goals.

Components:
1. **Sensors** — receive percepts from the environment
2. **World State** — model of how the world currently looks
3. **Goals** — desired outcome or state to be achieved
4. **Action Selection** — searches for action sequences that reach the goal
5. **Actuators** — carry out the chosen action

```
Environment
    ↓ (percepts)
  Sensors
    ↓
World State Model + Goals
    ↓
Action Selection
    ↓
  Actuators
    ↓ (actions)
Environment
```

**Advantage:** More flexible than reflex agents. Can handle a wider range of situations by planning sequences of actions toward a goal rather than reacting to percepts directly.

---

### Q.2(b) — Differentiate informed and uninformed search strategies. [3M]

**Uninformed Search Strategies**

Use only the information available in the problem definition (initial state, transitions, goal test). They have no idea how far they are from the goal.

Examples: BFS, DFS, Uniform Cost Search (UCS), Depth-Limited Search, Iterative Deepening

**Informed Search Strategies**

Use a heuristic function **h(n)** that estimates the cost from node n to the goal. This extra knowledge guides the search toward the goal more efficiently.

Examples: Greedy Best-First Search, A\* Search

**Comparison Table**

| Criterion | Uninformed Search | Informed Search |
|-----------|------------------|-----------------|
| Knowledge Used | Problem definition only | Problem + heuristic function h(n) |
| Examples | BFS, DFS, UCS | Greedy BFS, A\* |
| Efficiency | Lower (blindly explores) | Higher (guided by h(n)) |
| Completeness | Yes (BFS, UCS) | Yes (A\* with admissible h) |
| Optimality | UCS is optimal | A\* is optimal (admissible h) |
| Time/Space | Exponential in worst case | Better in practice |

Key advantage of informed search: reduces the number of nodes expanded by directing the search toward the goal, leading to significantly fewer operations in large state spaces.

---

### Q.3(a) — Explain A\* search algorithm with example. State the optimality condition. [2M]

**A\* Search Algorithm**

A\* combines UCS (optimal cost) and Greedy BFS (heuristic guidance). At each node n, it computes:

**f(n) = g(n) + h(n)**

- g(n) = actual cost from the start node to n
- h(n) = estimated cost from n to the goal (heuristic)
- f(n) = estimated total cost of solution through n

The algorithm always expands the node with the lowest f(n) value.

**Admissibility Condition (for Optimality)**

h(n) is admissible if: **h(n) ≤ h\*(n)** for all nodes n, where h\*(n) is the true cost to reach the goal. An admissible heuristic never overestimates.

**Worked Example**

Graph: S→A (g=2), S→B (g=5), A→B (g=1), A→G (g=10), B→G (g=3)
Heuristics: h(S)=5, h(A)=3, h(B)=3, h(G)=0

| Step | Node Expanded | Open List (f values) | Notes |
|------|--------------|---------------------|-------|
| 1 | S (f=5) | A(f=5), B(f=8) | Expand start |
| 2 | A (f=5) | B(f=6), G(f=12) | B updated: g=3 |
| 3 | B (f=6) | G(f=6) | G updated: g=6 |
| 4 | G (f=6) | — | GOAL reached! |

**Optimal path: S → A → B → G, total cost = 2 + 1 + 3 = 6**

Verify admissibility: h(S)=5≤6 ✓, h(A)=3≤4 ✓, h(B)=3≤3 ✓, h(G)=0 ✓

---

### Q.3(b) — Apply BFS and DFS on the given tree. Which finds G first? Why? [3M]

Given tree:
```
         S
        / \
       A   B
      / \   \
     C   D   E
          \
           G (goal)
```

**BFS — Breadth First Search** (FIFO queue, level by level)

| Step | Node Expanded | Queue (after expansion) | Level |
|------|--------------|------------------------|-------|
| 1 | S | A, B | 0 |
| 2 | A | B, C, D | 1 |
| 3 | B | C, D, E | 1 |
| 4 | C (leaf) | D, E | 2 |
| 5 | D | E, G | 2 |
| 6 | E (leaf) | G | 2 |
| 7 | F (leaf) | G | 2 |
| 8 | **G — GOAL!** | — | 3 |

BFS path to G: S → A → D → G (found at step 8, exploring 8 nodes)

**DFS — Depth First Search** (LIFO stack, goes deep first)

| Step | Node Expanded | Stack (after expansion) | Action |
|------|--------------|------------------------|--------|
| 1 | S | A, B | Push A,B; pop A |
| 2 | A | C, D, B | Push C,D; pop C |
| 3 | C (leaf) | D, B | No children; backtrack |
| 4 | D | G, B | Push G; pop G |
| 5 | **G — GOAL!** | — | Goal found! |

DFS path to G: S → A → D → G (found at step 5, exploring only 5 nodes)

**Conclusion**

DFS finds the goal G first (step 5 vs step 8). In this tree, G is located on the left-deep branch (D→G), which DFS reaches before BFS completes level 2. Both algorithms find the same path: S→A→D→G.

Note: DFS is NOT guaranteed to be faster in general — it depends on the position of the goal. DFS is also NOT optimal (may find a longer path if a shorter one exists).

---

### Q.4 — Minimax + Alpha-Beta Pruning on the given game tree. [5M]

**Given game tree:**
```
            Root (MAX)
           /           \
        Q (MIN)        R (MIN)
      / | | \          / | | \
     2  4  5  8       0  1  -1  -2
```

**Part 1 — Minimax Procedure**

Minimax computes the optimal strategy for a two-player zero-sum game. MAX maximizes, MIN minimizes.

**Step 1:** Evaluate MIN node Q (children: 2, 4, 5, 8)
```
Value(Q) = min(2, 4, 5, 8) = 2
```

**Step 2:** Evaluate MIN node R (children: 0, 1, −1, −2)
```
Value(R) = min(0, 1, −1, −2) = −2
```

**Step 3:** Evaluate MAX node Root (children: Q=2, R=−2)
```
Value(Root) = max(2, −2) = 2 → Optimal move: go to Q
```

**Optimal decision at root: Choose Q (value = 2)**

---

**Part 2 — Alpha-Beta Pruning**

Alpha-Beta eliminates branches that cannot affect the final minimax value.

- α = best value MAX can guarantee (initialized to −∞)
- β = best value MIN can guarantee (initialized to +∞)

**Trace:**

```
Root (MAX): α=−∞, β=+∞ → explore Q

  Q (MIN): α=−∞, β=+∞
    Leaf 2 → v=2, update β=2
    Leaf 4 → v=min(2,4)=2 (β unchanged)
    Leaf 5 → v=min(2,5)=2 (β unchanged)
    Leaf 8 → v=min(2,8)=2 (β unchanged)
    Q returns 2 → Root updates α = max(−∞,2) = 2

  R (MIN): α=2, β=+∞
    Leaf 0 → v=0, update β=0
    β(=0) ≤ α(=2) → β-cutoff! Prune leaves: 1, −1, −2
    R returns ≤ 0 (MAX will not choose R over 2)

Root = max(2, ≤0) = 2
```

**Pruned nodes: Leaves 1, −1, −2 under R (3 nodes pruned)**

**Final result: Optimal move is Root → Q, value = 2** (confirmed by both methods)

---

### Q.5(a) — Bayes' Theorem importance in AI. Law of Total Probability. [2M]

**Bayes' Theorem**

Bayes' Theorem provides a way to update the probability of a hypothesis h given observed data D:

**P(h | D) = P(D | h) × P(h) / P(D)**

- P(h) — **Prior**: probability of hypothesis h before seeing data
- P(D | h) — **Likelihood**: probability of data D given hypothesis h is true
- P(D) — **Marginal probability** of data D (normalizing constant)
- P(h | D) — **Posterior**: updated belief in h after seeing D

**Importance in AI**

1. Handles uncertainty: provides a principled way to reason under incomplete knowledge
2. Combines prior knowledge with observed evidence
3. Foundation for Bayesian classifiers, spam filters, medical diagnosis systems
4. Enables belief updating as new evidence arrives

**Example:** Medical test for a disease. Prior P(disease)=0.01. If test is 99% accurate: P(positive|disease)=0.99. After a positive test, Bayes gives the updated P(disease|positive) — which may still be low if the disease is rare.

**Law of Total Probability**

If A₁, A₂, ..., Aₙ form a partition of sample space S (mutually exclusive, exhaustive):

**P(B) = Σᵢ P(B | Aᵢ) × P(Aᵢ)**

This allows computing P(D) in Bayes' theorem by summing over all hypotheses:

**P(D) = Σₕ P(D | h) × P(h)**

---

### Q.5(b) — Naïve Bayes Classifier — classify (Red, SUV, Domestic) from stolen vehicle dataset. [3M]

**Dataset:**

| Color | Type | Origin | Stolen |
|-------|------|--------|--------|
| Red | Sports | Domestic | Yes |
| Red | Sports | Imported | Yes |
| Red | SUV | Imported | No |
| Yellow | Sports | Domestic | No |
| Yellow | SUV | Imported | Yes |
| Yellow | Sports | Domestic | Yes |
| Red | SUV | Imported | No |

Total instances = 7. Stolen=Yes: 4 (rows 1,2,5,6). Stolen=No: 3 (rows 3,4,7)

**Step 1 — Prior Probabilities**
```
P(Stolen = Yes) = 4/7 ≈ 0.571
P(Stolen = No) = 3/7 ≈ 0.429
```

**Step 2 — Likelihood Probabilities for (Red, SUV, Domestic)**

| Feature | Value | P(feature \| Yes) | P(feature \| No) |
|---------|-------|------------------|-----------------|
| Color | Red | 2/4 = 0.500 | 2/3 = 0.667 |
| Type | SUV | 1/4 = 0.250 | 2/3 = 0.667 |
| Origin | Domestic | 2/4 = 0.500 | 1/3 = 0.333 |

Derivation for Color=Red|Yes: Among Yes rows (1,2,5,6), Red appears in rows 1 and 2 → 2/4

Derivation for Type=SUV|Yes: Among Yes rows, SUV appears in row 5 only → 1/4

**Step 3 — Posterior Calculation (Naïve Bayes)**

```
P(Yes | Red, SUV, Domestic) ∝ P(Yes) × P(Red|Yes) × P(SUV|Yes) × P(Domestic|Yes)
= (4/7) × (2/4) × (1/4) × (2/4)
= (4/7) × (1/16)
= 4/112 = 1/28 ≈ 0.0357

P(No | Red, SUV, Domestic) ∝ P(No) × P(Red|No) × P(SUV|No) × P(Domestic|No)
= (3/7) × (2/3) × (2/3) × (1/3)
= (3/7) × (4/27)
= 12/189 = 4/63 ≈ 0.0635
```

**Step 4 — Normalize**
```
Total = 1/28 + 4/63 = 9/252 + 16/252 = 25/252

P(Stolen=Yes | Red, SUV, Domestic) = (9/252)/(25/252) = 9/25 = 0.36 (36%)
P(Stolen=No | Red, SUV, Domestic) = (16/252)/(25/252) = 16/25 = 0.64 (64%)
```

**Classification Decision: NOT STOLEN (P=0.64 > P=0.36)**

---

### Q.6(a) — Define CSP with components and list two real-world applications. [2M]

**Constraint Satisfaction Problem (CSP)**

A CSP is defined by three components:

1. **Variables (X):** A set of variables X = {X₁, X₂, ..., Xₙ} whose values must be determined
2. **Domains (D):** A domain Dᵢ for each variable Xᵢ specifying the set of possible values
3. **Constraints (C):** A set of constraints specifying allowable combinations of values for subsets of variables

A solution is an assignment of values to all variables such that all constraints are satisfied simultaneously.

**Example — Map Coloring:**
- Variables: {WA, NT, SA, Q, NSW, V, T} (Australian states)
- Domain: {Red, Green, Blue} for each variable
- Constraints: No two adjacent states may have the same color (WA≠NT, WA≠SA, NT≠Q, SA≠Q, SA≠NSW, SA≠V, Q≠NSW, NSW≠V)

**Backtracking Search:** Assigns one variable at a time; checks constraints; if violated, backtracks to previous variable.

**Real-World Applications**

1. **Scheduling** — university timetabling, exam scheduling (variables=classes, domains=time slots, constraints=no overlaps)
2. **Sudoku Puzzle** — variables=81 cells, domain={1..9}, constraints=row/column/block uniqueness

---

### Q.6(b) — Solve SEND + MORE = MONEY as a CSP. [3M]

**(i) Variables and Domains**

Variables: {S, E, N, D, M, O, R, Y} — one per unique letter (8 variables)

Domains: Dᵢ = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9} for each variable

**(ii) Constraints**

- **C1 Uniqueness:** All letters represent different digits (AllDifferent constraint)
- **C2:** S ≠ 0, M ≠ 0 (no leading zeros in any addend or result)
- **C3 Carry-based column arithmetic (right to left):**

```
Ones:      D + E = Y + 10 × C₁
Tens:      N + R + C₁ = E + 10 × C₂
Hundreds:  E + O + C₂ = N + 10 × C₃
Thousands: S + M + C₃ = O + 10 × C₄
Ten-thou:  C₄ = M (carry into new column)
```
where C₁, C₂, C₃, C₄ ∈ {0, 1} are carry digits.

**(iii) Deriving M and S using Backtracking**

From constraint C₄ = M and C₄ ∈ {0, 1}:
- Since M ≠ 0 → **M = 1** (the carry into the ten-thousands column must be 1)

Substitute M = 1 into the thousands column:
```
S + 1 + C₃ = O + 10 × C₄ = O + 10 (since C₄=M=1)
∴ S + C₃ = O + 9
```

**Case 1 (C₃ = 0):** S = O + 9. Since S ≤ 9 and O ≥ 0: **S = 9, O = 0**. Check O ≠ M(=1)? ✓

**Case 2 (C₃ = 1):** S = O + 8. For O ≥ 0 and O ≠ 1: S=9→O=1 (forbidden), S=8→O=0 ✓

∴ **S = 9** (most likely from Case 1 — leads to the known solution)

**Complete Solution (for reference):**

| S | E | N | D | M | O | R | Y | Verification |
|---|---|---|---|---|---|---|---|--------------|
| 9 | 5 | 6 | 7 | 1 | 0 | 8 | 2 | 9567 + 1085 = 10652 ✓ |

---

### Q.7(a) — What is ML? Explain Supervised, Unsupervised, and Reinforcement Learning. [2M]

**Machine Learning**

Machine Learning (ML) is a subfield of AI that gives computers the ability to learn from data and improve their performance on tasks without being explicitly programmed. Tom Mitchell: *'A program learns from experience E with respect to task T and measure P if its performance on T, as measured by P, improves with experience E.'*

**Three Major Categories**

**1. Supervised Learning**
- Training data contains input-output pairs (labeled data)
- Model learns a mapping function f: X → Y
- Goal: Predict the output for new, unseen inputs
- Examples of algorithms: Linear Regression, Decision Trees, SVM, Neural Networks
- *Real-world example: Email spam detection — model trained on emails labeled Spam/Not Spam*

**2. Unsupervised Learning**
- Training data has NO labels
- Model discovers hidden patterns or structure in the data
- Goal: Find clusters, associations, or compressed representations
- Examples: K-Means Clustering, PCA, Autoencoders
- *Real-world example: Customer segmentation — group customers by purchase behaviour*

**3. Reinforcement Learning**
- An agent interacts with an environment, receives rewards or penalties, and learns a policy that maximizes cumulative reward
- Goal: Learn optimal behaviour through trial-and-error
- Key concepts: State, Action, Reward, Policy, Q-value
- *Real-world example: Training a robot to walk — it receives reward when it moves forward*

---

### Q.7(b) — Least Square Regression — sales data. Estimate 2012 sales. [3M]

**Given Data** (re-coded years: 2005→1, 2006→2, ..., 2009→5)

| x | y (Sales, M$) | x² | xy |
|---|---------------|----|----|
| 1 | 12 | 1 | 12 |
| 2 | 19 | 4 | 38 |
| 3 | 29 | 9 | 87 |
| 4 | 37 | 16 | 148 |
| 5 | 45 | 25 | 225 |
| **Σ=15** | **Σ=142** | **Σ=55** | **Σ=510** |

**Step 2 — Compute Regression Coefficients** (n = 5)

```
a = (n·Σxy − Σx·Σy) / (n·Σx² − (Σx)²)
  = (5 × 510 − 15 × 142) / (5 × 55 − 15²)
  = (2550 − 2130) / (275 − 225)
  = 420 / 50 = 8.4

b = ȳ − a × x̄
  x̄ = 15/5 = 3,  ȳ = 142/5 = 28.4
  = 28.4 − 8.4 × 3 = 28.4 − 25.2 = 3.2
```

**Regression Line: y = 8.4x + 3.2**

**Step 3 — Estimate 2012 Sales**

For 2012: x = 2012 − 2004 = 8 (since x=1 corresponds to 2005)

```
y = 8.4 × 8 + 3.2 = 67.2 + 3.2 = 70.4 million dollars
```

**Estimated sales in 2012 = US$ 70.4 million**

---

## Assignment 1 Solutions (Total: 5 M)

---

### A1 — EM Algorithm — E-step & M-step with two-coin illustration. [2M]

**The EM (Expectation-Maximization) Algorithm**

EM is an iterative optimization algorithm for finding Maximum Likelihood Estimates (MLE) in models with latent (hidden) variables. It is used when some data is unobserved.

**E-Step — Expectation**

Given the current parameter estimates θ(t), compute the expected value (posterior probability) of the latent variable Z for each observation:

**Q(θ | θ(t)) = E_{Z|X, θ(t)} [log P(X, Z | θ)]**

In other words: for each observation, estimate the probability that it belongs to each hidden component.

**M-Step — Maximization**

Find the parameter values θ that maximize the expected log-likelihood computed in the E-step:

**θ(t+1) = argmax_θ Q(θ | θ(t))**

In other words: re-estimate the model parameters using the weighted counts from the E-step. Repeat until convergence (change in log-likelihood < threshold).

---

**Two-Coin Illustration**

Setup:
- Coin A: P(H) = 0.6, P(T) = 0.4
- Coin B: P(H) = 0.5, P(T) = 0.5
- Equal priors: P(A) = P(B) = 0.5
- Observations (coin identity unknown): H, T, H, H, T

**E-Step: Compute P(coin | toss outcome)**

For a Head (H):
```
P(H|A)·P(A) = 0.6 × 0.5 = 0.30
P(H|B)·P(B) = 0.5 × 0.5 = 0.25
Total = 0.55

P(A|H) = 0.30/0.55 = 6/11 ≈ 0.545 → Likely Coin A
P(B|H) = 0.25/0.55 = 5/11 ≈ 0.455
```

For a Tail (T):
```
P(T|A)·P(A) = 0.4 × 0.5 = 0.20
P(T|B)·P(B) = 0.5 × 0.5 = 0.25
Total = 0.45

P(A|T) = 0.20/0.45 = 4/9 ≈ 0.444 → Likely Coin B
P(B|T) = 0.25/0.45 = 5/9 ≈ 0.556
```

| Toss | Outcome | P(A\|obs) | P(B\|obs) | Most Likely Coin |
|------|---------|-----------|-----------|-----------------|
| 1 | H | 0.545 | 0.455 | Coin A |
| 2 | T | 0.444 | 0.556 | Coin B |
| 3 | H | 0.545 | 0.455 | Coin A |
| 4 | H | 0.545 | 0.455 | Coin A |
| 5 | T | 0.444 | 0.556 | Coin B |

**M-Step: Update Coin Parameters**

```
Expected H-count for Coin A = 0.545 + 0.545 + 0.545 = 1.636 (tosses 1,3,4)
Expected T-count for Coin A = 0.444 + 0.444 = 0.889 (tosses 2,5)

Updated P(H|A) = 1.636 / (1.636 + 0.889) = 1.636 / 2.525 ≈ 0.648 (was 0.60 → improving)
Similarly, P(H|B) updated from 0.50 to ≈ 0.551
```

Repeat until convergence.

---

### A2 — Design an AI Book Recommendation System for a college library. [2M]

**(i) Agent Design**

**Agent Type: Utility-Based Agent** (extends Goal-Based)

A utility-based agent is most appropriate because recommendations involve trade-offs: relevance vs. novelty vs. availability. The agent must maximize overall student satisfaction — a utility function — not just achieve a binary goal.

**PEAS Description:**

| Component | Description |
|-----------|-------------|
| **Performance** | Relevance of recommendations, user satisfaction rating, diversity, borrowing rate |
| **Environment** | Library database (books, availability), student profile, borrowing history, ratings |
| **Actuators** | Display screen (recommendation list), email/SMS notification, self-service kiosk |
| **Sensors** | Borrowing history scanner, search query input, explicit rating input, login authentication |

**(ii) Machine Learning Category**

**Recommended approach: Collaborative Filtering (Unsupervised Learning)**

Rationale: There is no pre-labeled 'good recommendation' data. The system must discover patterns in student behaviour — which books are borrowed together, which students have similar tastes.

Method: Represent each student as a vector of borrowing history. Compute similarity (cosine/Pearson). Recommend books that similar students borrowed.

Alternative: If explicit ratings are collected → Supervised approach (rating prediction). Hybrid systems combine both.

**(iii) Bayesian Recommendation Approach**

Using Naïve Bayes to recommend books based on past borrowing history:

**P(Like book B | Genre=G, Author=A, Topic=T) ∝ P(Like B) × P(G|Like) × P(A|Like) × P(T|Like)**

- Prior P(Like B): fraction of students who have borrowed similar books in the past
- P(Genre=Science|Like) = #books liked with Genre=Science / #books liked
- Apply Naïve Bayes independence assumption across features to compute posterior probability
- Recommend the top-K books with highest posterior probability of being liked by the current student

*Example:* A student who borrows AI textbooks → system computes P(Like new_ML_book | past_AI_books) and recommends it if above threshold.

---

### A3 — MDL Principle. Contrast with MAP hypothesis. [1M]

**Minimum Description Length (MDL) Principle**

MDL states that the best hypothesis h for a dataset D is the one that minimizes the total description length:

**MDL(h, D) = L(h) + L(D | h)**

- **L(h):** Number of bits needed to encode hypothesis h (model complexity — penalizes complex models)
- **L(D | h):** Number of bits needed to encode data D given that h is known (encoding error — favors models that fit the data well)

MDL therefore balances model fit against model complexity, naturally preventing overfitting.

**Connection to MAP (Maximum A Posteriori)**

MAP selects the hypothesis that maximizes the posterior probability:

**h_MAP = argmax_h P(h | D) = argmax_h [P(D | h) × P(h)]**

Taking the negative logarithm, maximizing P(D|h)×P(h) is equivalent to minimizing:

**−log P(D | h) − log P(h) ≡ L(D | h) + L(h) = MDL**

When the prior P(h) is the Shannon optimal code for h, MDL and MAP give identical results.

**When to Prefer MDL over MAP:**
1. No meaningful prior: If P(h) cannot be defined or estimated reliably, MDL uses description length as a substitute
2. Model interpretability: MDL directly quantifies model complexity — simpler models preferred
3. Avoiding overfitting: MDL penalizes overly complex models even when they fit training data perfectly

---

[← Back to Course Overview](/courses/paiml/) | [Preparation Guide](/courses/paiml/midterm-preparation-guide/)
