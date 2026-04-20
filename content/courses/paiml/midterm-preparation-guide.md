---
title: "PAIML I Mid-Term Examination Preparation Guide"
date: 2026-04-20
description: "Complete preparation guide for PAIML I Mid-Term exam covering AI foundations, search strategies, adversarial search, Bayesian learning and ML basics."
categories: ["Courses"]
tags: ["ai", "machine-learning", "mtech", "exam", "preparation"]
sidebar: false
build:
  list: never
  render: always
---

> This guide covers all important topics, expected question patterns, sample problems, and answer strategies for your upcoming I Mid examination. Questions in the exam are drawn from these areas — study each topic deeply rather than memorising exact questions.

---

## Syllabus Coverage & Topic Importance Map

| Topic / Concept | Importance |
|----------------|-----------|
| Agents: types, PEAS, architecture diagrams | ★★★★★ |
| Uninformed Search: BFS, DFS, UCS | ★★★★★ |
| Informed Search: A\*, Best-First, Hill Climbing | ★★★★☆ |
| Adversarial Search: Minimax algorithm | ★★★★★ |
| Alpha-Beta Pruning | ★★★★★ |
| Constraint Satisfaction Problems (CSP) | ★★★★☆ |
| Bayes' Theorem & Law of Total Probability | ★★★★★ |
| Naive Bayes Classifier (with dataset problems) | ★★★★★ |
| ML Categories: Supervised / Unsupervised / RL | ★★★☆☆ |
| Linear Regression (least squares) | ★★★★☆ |

---

## Part A — MCQ & Fill-in-the-Blank Preparation (1 Mark each)

> **Quick Revision Note:** Part A has 10 questions — 5 MCQs and 5 Fill-in-the-Blanks (FIBs). All carry 1 mark each. MCQs test conceptual knowledge — read all options; eliminate clearly wrong ones first. FIBs have a single missing word or phrase. Topics spread across: agents (CO1), search (CO1), adversarial search & Bayes (CO3), and ML basics (CO5).

### Agent Types

Know the four agent types by name: **Simple Reflex, Model-Based Reflex, Goal-Based, Utility-Based**. A FIB will give a description and ask for the name. Distinguish each by: Does it maintain state? Does it have goals? Does it use a utility function?

- **Simple Reflex agent** — no internal state, uses condition-action rules
- **Model-Based Reflex** — keeps an internal world model
- **Goal-Based** — searches for action sequences to achieve a goal
- **Utility-Based** — selects action that maximises a utility function

---

### Search Completeness & Optimality

MCQs will ask which search algorithm guarantees finding a solution (completeness) or the shortest/cheapest solution (optimality). Memorise this table:

| Algorithm | Complete | Optimal | Time |
|-----------|----------|---------|------|
| BFS | Yes | Yes (uniform cost) | O(b^d) |
| DFS | No (can loop) | No | O(b^m) |
| UCS | Yes | Yes (step costs ≥ 0) | O(b^C\*/ε) |
| A\* | Yes | Yes (if h admissible) | O(b^d) |

---

### A\* Admissibility (FIB)

A FIB will give the A\* formula **f(n) = g(n) + h(n)** and ask what property h(n) must satisfy. The word is **admissible** — meaning h(n) never overestimates the true cost h\*(n).

- Admissible heuristic: **h(n) ≤ h\*(n)** for all nodes n
- An admissible heuristic guarantees A\* finds the optimal solution

---

### Minimax Principle (MCQ)

MCQs describe what a MAX node or MIN node does. MAX node returns the maximum of its children; MIN node returns the minimum. The root is always a MAX node in standard game trees.

- MAX node = max of child values
- MIN node = min of child values
- Optimal strategy: MAX plays to maximise, MIN plays to minimise

---

### Alpha-Beta Pruning (FIB)

A FIB will say "Alpha-Beta pruning prunes subtrees that cannot affect the final ___ value" — the answer is **minimax** (or optimal).

- α = best value MAX can guarantee (α starts at −∞)
- β = best value MIN can guarantee (β starts at +∞)
- Prune when **β ≤ α** (beta cutoff at MIN node)

---

### Naive Bayes Assumption (MCQ)

The MCQ will ask why Naive Bayes is called 'naive'. The answer is the **conditional independence assumption** — all features are assumed independent given the class label.

- 'Naive' = features are conditionally independent given class
- Despite this strong assumption, Naive Bayes works well in practice

---

### Bayes' Theorem Terms (FIB)

A FIB will show P(h|D) ∝ P(D|h) × P(h) and ask what P(h) is called. The answer is the **Prior probability**.

- P(h) = **Prior** — belief before seeing data
- P(D|h) = **Likelihood** — how probable the data is under hypothesis h
- P(h|D) = **Posterior** — updated belief after seeing data

---

### CSP — Not a CSP (MCQ)

The MCQ will list problems and ask which is NOT a CSP. **Shortest-path problems** are typically NOT modelled as CSPs (they are search problems).

- CSP examples: map coloring, Sudoku, N-Queens, SEND+MORE=MONEY
- NOT CSP: shortest path, numeric optimisation without explicit constraint variables

---

### Reinforcement Learning (FIB)

A FIB will describe learning through rewards/penalties and ask what it is called. The answer is **Reinforcement Learning**.

- Reinforcement Learning: agent, environment, state, action, reward, policy
- Goal: learn a policy π that maximises cumulative reward

---

### Definition of Learning (MCQ)

The MCQ will ask what 'learning' means in ML. The correct answer: **improving task performance through past experience and data**. Reject: memorising training data, reducing complexity.

- Tom Mitchell's definition: A program learns from experience E w.r.t. task T if its performance P on T improves with E

---

## Part B — Unit-wise Topic Guide & Sample Problems (5 Marks each)

> **Quick Revision Note:** Part B has 6 questions — answer any 4. Each carries 5 marks. Questions Q2–Q3 are from Unit 1 (AI & Search). Q4–Q6 are from Unit 2 (Adversarial & Bayesian). Q7 is from Unit 3 intro (ML). Each question has two sub-parts (a) 2M and (b) 3M — OR one single 5M question.

---

## Unit 1 — Introduction to AI | Agents | Search Strategies

### Artificial Intelligence — Definition and Agent Architecture

Be ready to define AI in your own words (2–3 sentences). Explain the Turing Test, rational agent model, or the 'acting humanly vs. thinking humanly' distinction.

Know **goal-based agent architecture**: draw a block diagram showing Percepts → World State + Goals → Action Selection → Actions. Label each block and explain data flow.

**PEAS**: for any agent given (medical system, robot, taxi), identify: Performance measure, Environment, Actuators, Sensors.

---

**Q: Define AI and explain goal-based agent with a diagram**

For a goal-based agent — draw the internal block diagram and label: Sensors, Percepts, World State model, Goals, Action Selection mechanism, Actuators.

Explain data flow: percept updates world state → goal checked → action selection searches for goal-achieving action → actuators execute.

Contrast with simple reflex agent (no state, no goals — pure condition-action rules).

---

**Q: Explain PEAS for a self-driving car agent. Which agent type is most suitable and why?**

- Performance: safety, speed, fuel efficiency, legal compliance, passenger comfort
- Environment: roads, traffic, pedestrians, weather, GPS data
- Actuators: steering, brakes, accelerator, indicators, horn
- Sensors: cameras, LIDAR, ultrasonic, GPS, speedometer
- Agent type: **Utility-Based** — must balance multiple performance criteria (safety vs. speed vs. comfort) using a utility function.

---

### Search Strategies — Uninformed and Informed

Know these algorithms by heart: **BFS, DFS, UCS, A\*, Greedy Best-First, Hill Climbing**. For each: state completeness, optimality, time complexity, space complexity.

BFS vs DFS: BFS explores level-by-level (FIFO queue), finds shallowest goal. DFS dives deep (LIFO stack), may not find optimal solution. A\*: f(n) = g(n) + h(n). Admissibility of h(n) ≤ h\*(n) is the key condition for optimality.

---

**Q: Trace BFS and DFS on a small tree — which finds goal first?**

Given a tree (nodes S, A, B, C, D, E, F, G where G is goal), apply BFS and DFS.

BFS: show queue contents at each step — S → {A,B} → {B,C,D} → {C,D,E,F} → {D,E,F} → {E,F,G} → GOAL.

DFS: show stack at each step — S → A → C (dead end, backtrack) → D → G — GOAL found early.

Conclusion: state which finds goal first and explain why (position of goal in tree determines which is faster).

---

**Q: Explain A\* with example. State the admissibility condition.**

Draw a small graph with edge costs and h-values. Show f(n) = g(n) + h(n) for each node.

Trace: which node is expanded at each step? Show open list with f-values after each expansion.

State: **h(n) is admissible if h(n) ≤ h\*(n)**. Verify your h-values are admissible for your example.

---

**Q: What is Hill Climbing? What are the problems associated with it? How are they solved?**

Hill Climbing: always move to the highest-valued neighbour (steepest ascent) — a local search algorithm.

Problems:
1. **Local maxima** — gets stuck at peaks that are not the global maximum
2. **Ridges** — progress is slow because small steps don't make significant improvement
3. **Plateaus** — flat regions where all neighbours have equal value

Solutions: **Random restarts**, **Simulated Annealing** (accept worse moves with decreasing probability), **Beam search** (keep k best states).

---

## Unit 2 — Adversarial Search | CSP | Bayesian Learning

### Minimax Algorithm and Alpha-Beta Pruning

Minimax: two-player, zero-sum game. MAX maximises, MIN minimises. Backup values from leaves to root.

Steps: (1) Generate game tree to terminal nodes. (2) Assign utility values to leaves. (3) Back up: MIN returns minimum; MAX returns maximum. (4) Root's value = optimal move.

Alpha-Beta: same result as Minimax but prunes branches. α = best MAX can guarantee. β = best MIN can guarantee. Prune when **β ≤ α**.

---

**Q: Given a game tree with specific leaf values, apply Minimax and then Alpha-Beta Pruning**

A game tree will be given (typically 2–3 levels deep with numbered leaf values).

Minimax: compute values bottom-up. At MIN level: take minimum of children. At MAX level: take maximum.

Alpha-Beta: trace α and β values at each node. Show when pruning occurs (β ≤ α). Cross out pruned branches. Count how many nodes were pruned.

---

**Q: What is the time complexity of Minimax? How does Alpha-Beta improve it?**

- Minimax: **O(b^m)** where b = branching factor, m = maximum depth
- Alpha-Beta best case: **O(b^(m/2))** — effectively doubles the depth searchable in the same time
- Best case occurs when moves are ordered best-first (optimal ordering)
- Practical improvement: Alpha-Beta allows searching roughly **twice as deep** as Minimax for the same computation budget

---

### Constraint Satisfaction Problems (CSP)

CSP defined by: Variables X = {X1,...,Xn}, Domains D = {D1,...,Dn}, Constraints C. A solution is a complete, consistent assignment satisfying all constraints.

Know two types of CSP problems well:
1. **Map Coloring** — variables=regions, domain=colors, constraint=adjacent≠same
2. **Cryptarithmetic** — variables=letters, domain=0-9, constraints=algebraic equations + uniqueness

Backtracking Search: assign one variable at a time; check constraints; if violated, backtrack.

---

**Q: Model and solve a cryptarithmetic puzzle as a CSP**

For a puzzle like SEND + MORE = MONEY — define: variables {S,E,N,D,M,O,R,Y}, domain {0-9} each, constraint AllDifferent + column-wise arithmetic equations + leading zeros constraint.

Show column-by-column constraint derivation (ones column: D+E = Y + 10×C1, etc.).

Use the carry constraint to fix M=1 (since carry out of thousands column is 1). Then derive S.

---

### Bayesian Learning — Bayes' Theorem and Naive Bayes Classifier

Bayes' Theorem: **P(h|D) = P(D|h)×P(h) / P(D)**. Know what each term is called: Prior, Likelihood, Posterior, Evidence.

Law of Total Probability: **P(D) = Σ P(D|hi)×P(hi)** over all hypotheses.

Naive Bayes: assumes features are conditionally independent given the class. To classify a new instance X = (x1, x2, ..., xn): compute **P(class|X) ∝ P(class) × ∏ P(xi | class)**. Choose class with highest posterior.

---

**Q: Apply Naive Bayes Classifier to a small dataset**

A table with 7–14 rows will be given. Each row has feature columns and a class column.

Steps:
1. Count class frequencies → compute prior P(Yes) and P(No)
2. For each feature value of the new instance, count occurrences within each class → compute likelihood P(feature|class)
3. Multiply: posterior ∝ prior × product of likelihoods
4. Compare: the class with higher (unnormalised) posterior wins

Optionally normalise to get actual probabilities (divide by the sum of both posteriors).

---

**Q: What is a Bayesian Belief Network (BBN)? How does it represent conditional independence?**

BBN is a directed acyclic graph (DAG) where nodes represent random variables and edges represent conditional dependencies.

A node is conditionally independent of its non-descendants given its parents (Markov condition).

Each node has a **Conditional Probability Table (CPT)** giving P(node | parents).

Example: Alarm → Burglary, Alarm → Earthquake. P(Burglary|Alarm) computed from the CPT without needing full joint distribution.

---

## Unit 3 — Introduction to Machine Learning | Regression

### Machine Learning — Types and Applications

Know the three paradigms:
- **Supervised Learning** — labeled data, learn X→Y
- **Unsupervised Learning** — unlabeled data, find patterns
- **Reinforcement Learning** — agent-environment interaction, reward signal

Differences: training data type (labeled/unlabeled/reward), feedback type (direct/none/delayed), goal (prediction/structure discovery/policy). Give one real-world example for each type.

---

### Linear Regression — Least Squares Method

Regression line: **y = ax + b**

Least squares formulas:
```
a = (n·Σxy − Σx·Σy) / (n·Σx² − (Σx)²)
b = ȳ − a×x̄
```

Steps: (1) Tabulate x, y, x², xy. (2) Compute sums. (3) Substitute into formulas. (4) Write the line. (5) Substitute target x to predict y.

> **IMPORTANT:** If years are given (2005, 2006, ...), re-code as x = 1, 2, 3, ... to avoid large numbers. Always re-map back when predicting.

---

## Quick Revision Checklist — Night Before the Exam

| Topic | Self-Test Question |
|-------|-------------------|
| **Agent Types** | Can you name all 4 agent types and explain the difference in one sentence each? |
| **PEAS** | Can you construct PEAS for a new agent (e.g., a chess-playing program)? |
| **Search Properties** | Can you fill: BFS (Complete=Y, Optimal=Y), DFS (N,N), UCS (Y,Y), A\* (Y,Y if admissible)? |
| **A\* Formula** | f(n) = g(n) + h(n). Can you state admissibility? Can you trace A\* on a 4-node example? |
| **Minimax** | Can you evaluate a 2-level game tree (MAX→MIN→leaves) in under 2 minutes? |
| **Alpha-Beta** | Can you trace α and β at every node and identify pruned branches? |
| **CSP** | Can you define variables, domains, constraints for Map Coloring and SEND+MORE=MONEY? |
| **Bayes Theorem** | Can you state the formula and explain: prior, likelihood, posterior, evidence? |
| **Naive Bayes** | Can you compute P(class|features) from a 7-row table without a calculator? |
| **ML Types** | Can you distinguish Supervised/Unsupervised/RL with one real example each? |
| **Regression** | Can you compute a and b using the summation table formulas from 5 data points? |

---

## Exam-Day Strategy Tips

**Time Management (2-hour exam, 30 marks)**

- **Part A (10M):** Target 20 minutes. 2 minutes per question. Don't overthink MCQs — go with your first instinct.
- **Part B (20M):** 100 minutes for 4 questions = 25 minutes per question. Spend 5 min planning, 18 min writing, 2 min reviewing.
- Choosing Part B questions: attempt the ones you are most confident about first. Do NOT attempt all 6.

**Answer Writing Strategy**

- **Diagrams:** draw a neat diagram for any architecture or tree question. A labelled diagram earns marks even if explanation is incomplete.
- **Tables:** use comparison tables wherever possible (e.g., BFS vs DFS vs UCS). Tables are compact and score well.
- **Numerical problems:** always show all working. If the final answer is wrong but the method is correct, you will receive partial marks.
- **Definitions:** keep definitions to 2–3 concise lines. Do not write paragraphs for definition questions.
- State conclusions explicitly: *"Therefore, the optimal move is Root → Q with value = 2."*

---

**Best of luck in your examination!**

[← Back to Course Overview](/courses/paiml/)
