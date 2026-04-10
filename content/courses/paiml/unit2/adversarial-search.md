---
title: "2.1 Adversarial Search"
date: 2026-02-01
description: "Optimal decisions in games, minimax algorithm, alpha-beta pruning and constraint satisfaction problems for M.Tech PAIML."
categories: ["Courses"]
tags: ["adversarial-search", "minimax", "alpha-beta", "csp", "games", "mtech"]
build:
  list: never
  render: always
---

## What is Adversarial Search?

Adversarial search deals with competitive environments where agents have conflicting goals. Used in two-player zero-sum games like chess, checkers, tic-tac-toe.

**Zero-sum game:** One player's gain is the other's loss.

### Key Terms

| Term | Meaning |
|------|---------|
| **MAX player** | Wants to maximize the utility |
| **MIN player** | Wants to minimize the utility |
| **Terminal state** | End of game |
| **Utility function** | Numeric value of terminal state |
| **Ply** | One level in game tree |

## Minimax Algorithm

Minimax computes the optimal strategy for MAX assuming MIN plays optimally.

### Algorithm

```
function MINIMAX-VALUE(state):
  if TERMINAL-TEST(state):
    return UTILITY(state)
  if MAX's turn:
    return max over successors of MINIMAX-VALUE(successor)
  if MIN's turn:
    return min over successors of MINIMAX-VALUE(successor)
```

### Example — Tic-Tac-Toe

```
         MAX
        /    \
      MIN    MIN
     / \    / \
   +1  -1  0  +1

MAX chooses: max(min(+1,-1), min(0,+1))
           = max(-1, 0)
           = 0
```

### Properties

| Property | Value |
|----------|-------|
| **Complete?** | Yes (finite game tree) |
| **Optimal?** | Yes (against optimal opponent) |
| **Time Complexity** | O(b^m) |
| **Space Complexity** | O(bm) |

**Problem:** Exponential time — chess has ~35^80 nodes. Cannot search entire tree.

## Alpha-Beta Pruning

Improves minimax by pruning branches that cannot affect the final decision.

### Key Variables
- **α (alpha):** Best value MAX can guarantee (starts at -∞)
- **β (beta):** Best value MIN can guarantee (starts at +∞)

### Pruning Rules
- **Prune at MIN node:** If value ≤ α → stop (MAX already has better)
- **Prune at MAX node:** If value ≥ β → stop (MIN already has better)

### Algorithm

```
function ALPHA-BETA(state, α, β, player):
  if TERMINAL(state):
    return UTILITY(state)
    
  if player = MAX:
    v = -∞
    for each successor s:
      v = max(v, ALPHA-BETA(s, α, β, MIN))
      α = max(α, v)
      if α ≥ β: break  ← β cutoff
    return v
    
  if player = MIN:
    v = +∞
    for each successor s:
      v = min(v, ALPHA-BETA(s, α, β, MAX))
      β = min(β, v)
      if β ≤ α: break  ← α cutoff
    return v
```

### Example

```
         MAX (α=-∞, β=+∞)
        /         \
    MIN(3)        MIN
   / | \          / \
  3  5  2        [pruned]
  
After left subtree: α=3
At right MIN node: first child = 1 < α=3 → prune rest
```

### Performance

| Ordering | Nodes Examined |
|----------|---------------|
| Worst case | O(b^m) — no pruning |
| Random | O(b^(3m/4)) |
| **Best case** | **O(b^(m/2))** — effective branching factor √b |

**Best case:** With perfect move ordering, alpha-beta searches **twice as deep** as minimax in the same time!

## Constraint Satisfaction Problems (CSP)

A CSP is defined by:
- **Variables:** X = {X1, X2, ..., Xn}
- **Domains:** D = {D1, D2, ..., Dn}
- **Constraints:** C = {C1, C2, ..., Cm}

**Goal:** Find assignment of values to variables satisfying all constraints.

### Example: Map Coloring

```
Variables: WA, NT, Q, NSW, V, SA, T
Domains: {Red, Green, Blue}
Constraints: Adjacent regions must have different colors

WA ≠ NT, WA ≠ SA
NT ≠ Q, NT ≠ SA
Q ≠ NSW, Q ≠ SA
NSW ≠ V, NSW ≠ SA
V ≠ SA

Solution: WA=Red, NT=Green, Q=Red, NSW=Green, V=Red, SA=Blue, T=Red
```

### Backtracking for CSP

```
function BACKTRACKING(assignment, csp):
  if assignment is complete: return assignment
  var = SELECT-UNASSIGNED-VARIABLE(csp)
  for each value in ORDER-DOMAIN-VALUES(var, csp):
    if value consistent with assignment:
      add {var=value} to assignment
      result = BACKTRACKING(assignment, csp)
      if result ≠ failure: return result
      remove {var=value} from assignment
  return failure
```

### Constraint Propagation

**Arc Consistency (AC-3):**
```
X → Y is arc consistent if for every value in Domain(X),
there exists a value in Domain(Y) satisfying the constraint.
```

## Practice Questions

**Short Answer (2 marks each)**

1. What is a zero-sum game? Give two examples.
2. Define alpha and beta in alpha-beta pruning.
3. What is a CSP? Give an example.
4. What is arc consistency?

**Long Answer (8 marks each)**

1. Explain the minimax algorithm with a complete example. What are its limitations?
2. Describe alpha-beta pruning. How does it improve upon minimax? Illustrate with an example showing pruned branches.
3. What are Constraint Satisfaction Problems? Solve the map-coloring problem using backtracking.

**Think & Apply**

1. Draw a game tree for tic-tac-toe with X to move. Apply minimax to find the optimal move.
2. Apply alpha-beta pruning to the following game tree and identify which branches are pruned:
```
Leaf values (left to right): 3, 5, 2, 9, 1, 4, 8, 6
```

[← Unit 2 Overview](/courses/paiml/unit2/) | [Next: Bayesian Learning →](/courses/paiml/unit2/bayesian-learning/)
