---
title: "1.2 Uninformed Search Strategies"
date: 2026-02-01
description: "Complete notes on uninformed search strategies - BFS, DFS, Uniform-cost search with examples and practice questions for M.Tech PAIML."
categories: ["Courses"]
tags: ["search", "bfs", "dfs", "uniform-cost", "ai", "mtech"]
_build:
  list: never
  render: always
---

## What is Search in AI?

Search is the process of finding a sequence of actions that leads from an initial state to a goal state. It is fundamental to AI problem solving.

### Key Components of a Search Problem

| Component | Description | Example (Romania Map) |
|-----------|-------------|----------------------|
| **Initial State** | Starting point | Arad |
| **Actions** | Possible moves from a state | Go to Zerind, Sibiu, Timisoara |
| **Transition Model** | Result of an action | Go(Arad, Zerind) → Zerind |
| **Goal Test** | Is this the goal? | At Bucharest? |
| **Path Cost** | Cost of reaching state | Distance in km |

### Solution
A sequence of actions leading from initial state to goal state. An **optimal solution** has the lowest path cost.

## Uninformed Search Strategies

Uninformed (blind) search has no additional information beyond the problem definition. It does not know whether one non-goal state is "better" than another.

## 1. Breadth-First Search (BFS)

Expands the shallowest unexpanded node first.

### Algorithm
```
1. Initialize queue with initial state
2. Loop:
   a. If queue is empty → return FAILURE
   b. Pop node from front of queue
   c. If node is GOAL → return solution
   d. Expand node, add children to BACK of queue
```

### Example
```
Initial: A
Goal: G

Tree:
        A
      /   \
     B     C
    / \   / \
   D   E F   G

BFS Order: A → B → C → D → E → F → G ✓
```

### Properties

| Property | Value |
|----------|-------|
| **Complete?** | Yes (if branching factor b is finite) |
| **Optimal?** | Yes (if path cost = 1 per step) |
| **Time Complexity** | O(b^d) |
| **Space Complexity** | O(b^d) — keeps all nodes in memory |

**Limitation:** Memory intensive — stores all nodes at current depth.

## 2. Uniform-Cost Search (UCS)

Expands the node with the lowest path cost g(n). Generalizes BFS for varying step costs.

### Algorithm
```
1. Initialize priority queue with initial state (cost=0)
2. Loop:
   a. If queue is empty → return FAILURE
   b. Pop node with LOWEST cost
   c. If node is GOAL → return solution
   d. Expand node, add children to priority queue with updated cost
```

### Example
```
A --1-- B --2-- D
|               |
4               1
|               |
C ------3------ G

UCS: A(0) → B(1) → C(4) → D(3) → G(4) ✓
Path: A → B → D → G, Cost = 4
```

### Properties

| Property | Value |
|----------|-------|
| **Complete?** | Yes (if step costs ≥ ε > 0) |
| **Optimal?** | Yes |
| **Time Complexity** | O(b^(1+C*/ε)) |
| **Space Complexity** | O(b^(1+C*/ε)) |

## 3. Depth-First Search (DFS)

Expands the deepest unexpanded node first.

### Algorithm
```
1. Initialize stack with initial state
2. Loop:
   a. If stack is empty → return FAILURE
   b. Pop node from TOP of stack
   c. If node is GOAL → return solution
   d. Expand node, add children to TOP of stack
```

### Example
```
Tree:
        A
      /   \
     B     C
    / \   / \
   D   E F   G

DFS Order: A → B → D → E → C → F → G ✓
```

### Properties

| Property | Value |
|----------|-------|
| **Complete?** | No (fails in infinite spaces) |
| **Optimal?** | No |
| **Time Complexity** | O(b^m) where m = max depth |
| **Space Complexity** | O(bm) — linear space! |

**Advantage:** Much less memory than BFS.

## Comparison of Uninformed Search Strategies

| Criterion | BFS | UCS | DFS |
|-----------|-----|-----|-----|
| Complete | Yes | Yes | No |
| Optimal | Yes* | Yes | No |
| Time | O(b^d) | O(b^C*/ε) | O(b^m) |
| Space | O(b^d) | O(b^C*/ε) | O(bm) |
| Best for | Shallow goals | Varying costs | Memory constraint |

*BFS optimal only when all step costs are equal.

## Depth-Limited Search

DFS with a depth limit l — prevents infinite loops.

```
DFS-Limited(problem, limit):
  return Recursive-DLS(initial_state, limit)

Recursive-DLS(node, limit):
  if GOAL-TEST(node) → return solution
  if limit = 0 → return cutoff
  for each action in ACTIONS(node):
    child = RESULT(node, action)
    result = Recursive-DLS(child, limit-1)
    if result ≠ cutoff → return result
  return cutoff
```

## Iterative Deepening DFS (IDDFS)

Combines advantages of BFS and DFS:
- Runs DFS with limit l = 0, 1, 2, 3...
- Complete like BFS, memory-efficient like DFS

| Property | Value |
|----------|-------|
| Complete | Yes |
| Optimal | Yes (uniform step cost) |
| Time | O(b^d) |
| Space | O(bd) |

## Practice Questions

**Short Answer (2 marks each)**

1. What is uninformed search? How does it differ from informed search?
2. Define completeness and optimality of a search algorithm.
3. Why is DFS not complete? Give an example.
4. What is the advantage of UCS over BFS?

**Long Answer (8 marks each)**

1. Explain BFS with algorithm, example and time/space complexity analysis.
2. Compare BFS, DFS and UCS with respect to completeness, optimality, time and space complexity.
3. What is Iterative Deepening DFS? How does it combine advantages of BFS and DFS?

**Think & Apply**

1. Apply BFS and DFS on this tree and trace the node expansion order:
```
        S
      / | \
     A  B  C
    /\     |
   D  E    F
            |
            G (goal)
```

2. You need to find the shortest path in a road network with different distances. Which search strategy would you use? Why?

[← Introduction to AI](/courses/paiml/unit1/introduction-to-ai/) | [Next: Informed Search →](/courses/paiml/unit1/informed-search/)
