---
title: "1.3 Informed Search Strategies"
date: 2026-02-01
description: "Complete notes on informed search - heuristic functions, greedy best-first search and A* search with examples for M.Tech PAIML."
categories: ["Courses"]
tags: ["search", "heuristic", "a-star", "greedy", "informed-search", "mtech"]
_build:
  list: never
  render: always
---

## What is Informed Search?

Informed (heuristic) search uses problem-specific knowledge beyond the problem definition to find solutions more efficiently than uninformed strategies.

The key idea: use a **heuristic function h(n)** to estimate the cost from node n to the goal.

## Heuristic Functions

A heuristic function **h(n)** estimates the cost of the cheapest path from node n to the goal.

### Properties of a Good Heuristic

**Admissibility:** h(n) never overestimates the actual cost to the goal.
```
h(n) ≤ h*(n)   where h*(n) = true cost to goal
```

**Consistency (Monotonicity):** For every node n and successor n':
```
h(n) ≤ c(n, a, n') + h(n')
```

### Example: Romania Map Problem

**h_SLD = Straight-line distance to Bucharest**

| City | h_SLD |
|------|-------|
| Arad | 366 |
| Bucharest | 0 |
| Craiova | 160 |
| Fagaras | 176 |
| Sibiu | 253 |
| Zerind | 374 |

h_SLD is admissible because straight-line distance never overestimates road distance.

## Greedy Best-First Search

Expands the node that appears closest to the goal based on h(n).

### Algorithm
```
1. Initialize priority queue with initial state
2. Evaluate f(n) = h(n) for each node
3. Expand node with MINIMUM h(n)
4. Repeat until goal found or failure
```

### Example
```
Arad → Sibiu (h=253) → Fagaras (h=176) → Bucharest (h=0) ✓
```

### Properties

| Property | Value |
|----------|-------|
| **Complete?** | No (can get stuck in loops) |
| **Optimal?** | No |
| **Time Complexity** | O(b^m) |
| **Space Complexity** | O(b^m) |

**Problem:** Greedy search ignores the actual cost already paid — can lead to suboptimal paths.

## A* Search

Combines actual cost g(n) and heuristic estimate h(n):

```
f(n) = g(n) + h(n)

where:
  g(n) = cost from start to n (actual)
  h(n) = estimated cost from n to goal
  f(n) = estimated total cost through n
```

### Algorithm
```
1. Initialize priority queue with initial state, f = h(start)
2. Loop:
   a. Pop node with MINIMUM f(n)
   b. If GOAL → return solution
   c. For each successor n':
      g(n') = g(n) + step_cost
      f(n') = g(n') + h(n')
      Add n' to queue
```

### Example — Romania Map

**Finding path from Arad to Bucharest:**

| Step | Node | g(n) | h(n) | f(n) |
|------|------|------|------|------|
| 1 | Arad | 0 | 366 | 366 |
| 2 | Sibiu | 140 | 253 | 393 |
| 3 | Rimnicu | 220 | 193 | 413 |
| 4 | Fagaras | 239 | 176 | 415 |
| 5 | Pitesti | 317 | 100 | 417 |
| 6 | **Bucharest** | 418 | 0 | **418** |

**Optimal path:** Arad → Sibiu → Rimnicu → Pitesti → Bucharest (418 km)

### Properties

| Property | Value |
|----------|-------|
| **Complete?** | Yes |
| **Optimal?** | Yes (if h is admissible) |
| **Time Complexity** | Exponential O(b^d) |
| **Space Complexity** | O(b^d) — keeps all nodes |

### Why A* is Optimal

**Theorem:** If h(n) is admissible, A* is optimal.

**Proof sketch:**
- Suppose suboptimal goal G2 is in queue with f(G2) = g(G2) > C* (optimal cost)
- Let n be a node on optimal path
- f(n) = g(n) + h(n) ≤ C* (since h is admissible)
- Therefore A* will expand n before G2 → finds optimal solution first

## Comparison: Greedy vs A*

| Aspect | Greedy Best-First | A* |
|--------|------------------|-----|
| Evaluation | f(n) = h(n) | f(n) = g(n) + h(n) |
| Complete | No | Yes |
| Optimal | No | Yes (admissible h) |
| Speed | Faster | Slower |
| Memory | Less | More |

## Designing Heuristics

### Relaxed Problems
A relaxed problem has fewer restrictions than the original. The optimal solution cost of a relaxed problem is an admissible heuristic.

**Example — 8-puzzle:**
- Original: A tile can move to adjacent empty square
- Relaxation 1: A tile can move anywhere → h = number of misplaced tiles
- Relaxation 2: A tile can move to any adjacent square → h = Manhattan distance

**Manhattan Distance:**
```
h(n) = Σ |row_i - goal_row_i| + |col_i - goal_col_i|
```

### 8-Puzzle Example

```
Current State:    Goal State:
7  2  4           1  2  3
5  0  6           4  5  6
8  3  1           7  8  0

Misplaced tiles h1 = 6 (tiles 7,2,5,6,8,3 are misplaced)

Manhattan distance h2:
  tile 7: |2-2| + |0-1| = 1
  tile 2: |0-0| + |1-1| = 0
  tile 4: |0-0| + |2-2| = 0
  tile 5: |1-1| + |0-0| = 0  (wait, 5 is at wrong position)
  ...
  h2 = 18 (more accurate than h1)
```

**h2 dominates h1:** h2(n) ≥ h1(n) for all n → h2 is the better heuristic.

## Practice Questions

**Short Answer (2 marks each)**

1. What is a heuristic function? What properties should it have?
2. Define admissibility of a heuristic. Why is it important?
3. What is the evaluation function used in A* search?
4. Why is greedy best-first search not optimal?

**Long Answer (8 marks each)**

1. Explain A* search algorithm with a suitable example. Prove that A* is optimal when the heuristic is admissible.
2. Compare greedy best-first search and A* search with respect to completeness, optimality, time and space complexity.
3. What are relaxed problems? How are they used to design admissible heuristics? Illustrate with the 8-puzzle problem.

**Think & Apply**

1. For the following graph, apply A* search to find the optimal path from S to G:
```
S --1-- A --2-- G (h: S=5, A=3, G=0)
|               |
3               1
|               |
B ------2------ C (h: B=4, C=2)
```

2. Given an 8-puzzle configuration, calculate h1 (misplaced tiles) and h2 (Manhattan distance). Which is a better heuristic and why?

[← Uninformed Search](/courses/paiml/unit1/uninformed-search/) | [Next: Unit 2 →](/courses/paiml/unit2/)
