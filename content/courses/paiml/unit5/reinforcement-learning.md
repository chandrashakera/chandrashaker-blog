---
title: "5.2 Reinforcement Learning"
date: 2026-02-01
sidebar: false
description: "Reinforcement learning, Q-learning, temporal difference learning and dynamic programming for M.Tech PAIML."
categories: ["Courses"]
tags: ["reinforcement-learning", "q-learning", "temporal-difference", "markov", "mtech"]
build:
  list: never
  render: always
---

## What is Reinforcement Learning?

Reinforcement Learning (RL) is learning through **interaction** — an agent learns to make decisions by receiving rewards and penalties from its environment.

```
Agent ──action──→ Environment
  ↑                    |
  └──state + reward────┘
```

**Key difference from supervised learning:**
- No labeled examples
- Learns from delayed rewards
- Must explore to discover good actions

## The Learning Task

### Formal Definition

An RL problem is a **Markov Decision Process (MDP):**

```
MDP = (S, A, T, R, γ)

S = set of states
A = set of actions
T(s,a,s') = transition probability P(s'|s,a)
R(s,a,s') = reward function
γ = discount factor (0 ≤ γ ≤ 1)
```

### Key Concepts

| Concept | Symbol | Meaning |
|---------|--------|---------|
| **Policy** | π(s) | Strategy — action to take in state s |
| **Value function** | V(s) | Expected cumulative reward from state s |
| **Q-function** | Q(s,a) | Expected reward for action a in state s |
| **Return** | G | Total discounted future reward |

### Discounted Return

```
Gₜ = rₜ + γrₜ₊₁ + γ²rₜ₊₂ + ... = Σ γᵏrₜ₊ₖ

γ = 0: Only immediate reward matters
γ = 1: All future rewards equally important
γ = 0.9: Common practical choice
```

## Markov Property

**"The future depends only on the present, not the past"**

```
P(sₜ₊₁ | sₜ, aₜ, sₜ₋₁, aₜ₋₁, ...) = P(sₜ₊₁ | sₜ, aₜ)
```

This simplifies RL — we only need current state, not full history.

## Value Functions

### State Value Function V^π(s)

Expected return starting from state s, following policy π:

```
V^π(s) = E[Gₜ | Sₜ=s, π]
        = E[rₜ + γV^π(sₜ₊₁) | Sₜ=s, π]   (Bellman equation)
```

### Action Value Function Q^π(s,a)

Expected return starting from state s, taking action a, then following π:

```
Q^π(s,a) = E[Gₜ | Sₜ=s, Aₜ=a, π]
          = R(s,a) + γ Σs' T(s,a,s') V^π(s')
```

### Bellman Optimality Equations

```
V*(s) = max_a [R(s,a) + γ Σs' T(s,a,s') V*(s')]

Q*(s,a) = R(s,a) + γ Σs' T(s,a,s') max_a' Q*(s',a')

Optimal policy: π*(s) = argmax_a Q*(s,a)
```

## Q-Learning

Q-learning is a **model-free** RL algorithm — learns Q-values directly from experience.

### Q-Learning Update Rule

```
Q(s,a) ← Q(s,a) + α[r + γ max_a' Q(s',a') - Q(s,a)]

where:
  α = learning rate
  r = immediate reward
  γ = discount factor
  max_a' Q(s',a') = best future value
  [r + γ max_a' Q(s',a') - Q(s,a)] = TD error
```

### Q-Learning Algorithm

```
Initialize Q(s,a) = 0 for all s,a

For each episode:
  Initialize state s
  
  Repeat until terminal:
    Choose action a using ε-greedy policy:
      With probability ε: random action (exploration)
      With probability 1-ε: argmax_a Q(s,a) (exploitation)
    
    Take action a, observe reward r and next state s'
    
    Q(s,a) ← Q(s,a) + α[r + γ max_a' Q(s',a') - Q(s,a)]
    
    s ← s'
```

### Example: Grid World

```
Grid (4×4):
S = Start, G = Goal (+1), F = Fire (-1), _ = Empty

S _ _ _
_ _ _ F
_ F _ _
_ _ _ G

Actions: Up, Down, Left, Right
Rewards: +1 at G, -1 at F, -0.01 otherwise
γ = 0.9, α = 0.1, ε = 0.1
```

**Q-table (initialized to 0, after training):**

| State | Up | Down | Left | Right |
|-------|-----|------|------|-------|
| S(0,0) | 0 | 0.1 | 0 | 0.3 |
| (0,1) | 0 | 0.2 | 0.1 | 0.4 |
| ... | | | | |
| (3,3)=G | 0 | 0 | 0 | 0 |

**Optimal path derived from Q-table:** S → Right → Right → Right → Down → Down → Down → G

## Non-Deterministic Rewards and Actions

Real environments are stochastic — same action may lead to different outcomes.

```
T(s, a, s') = P(s'|s,a) ≠ always 1

Example: Robot with 80% chance of moving correctly,
         10% chance of drifting left, 10% right
```

**Q-learning still converges** under certain conditions even with stochastic transitions.

## Temporal Difference Learning

TD learning updates estimates based on **other estimates** (bootstrapping).

### TD(0)

```
V(s) ← V(s) + α[r + γV(s') - V(s)]

TD error: δ = r + γV(s') - V(s)
```

### TD vs Monte Carlo

| Method | Update When | Variance | Bias |
|--------|------------|----------|------|
| Monte Carlo | End of episode | High | Low |
| TD(0) | Every step | Low | High |
| TD(λ) | Every step | Middle | Middle |

### TD(λ) — Eligibility Traces

Combines TD and Monte Carlo with parameter λ:

```
λ = 0: Pure TD(0)
λ = 1: Pure Monte Carlo

Eligibility trace: eₜ(s) = γλeₜ₋₁(s) + 1[Sₜ=s]
Update: V(s) ← V(s) + α × δₜ × eₜ(s)
```

## Generalizing from Examples

**Problem:** State space too large to store Q-value for every state.

**Solution:** Use function approximation:

```
Q(s,a) ≈ Q(s,a;θ)    where θ = parameters

Options:
- Linear: Q(s,a;θ) = θᵀφ(s,a)
- Neural Network (Deep Q-Network / DQN)
```

### Deep Q-Network (DQN)

Uses a neural network to approximate Q-values:

```
Input: State s (e.g., game pixels)
Output: Q(s,a) for all actions a

Loss: L(θ) = E[(r + γ max_a' Q(s',a';θ⁻) - Q(s,a;θ))²]

Key innovations:
  - Experience replay: Store and sample past transitions
  - Target network: Separate network for stable targets
```

**DQN achieved superhuman performance on 49 Atari games (DeepMind, 2015)**

## Relationship to Dynamic Programming

| Method | Model? | Update | When |
|--------|--------|--------|------|
| Dynamic Programming | Yes | Full Bellman | Offline |
| Monte Carlo | No | After episode | After episode |
| TD Learning | No | Bellman approx | Every step |

**Dynamic programming** (Value Iteration):
```
V(s) ← max_a [R(s,a) + γ Σs' T(s,a,s') V(s')]

Requires known T and R — not always available.
```

**Q-learning** works without knowing T and R — **model-free**.

## Exploration vs Exploitation

**Key dilemma:** Should the agent explore new actions or exploit known good ones?

### ε-Greedy Policy

```
With probability ε: random action (explore)
With probability 1-ε: best known action (exploit)

Common: Start with ε=1.0, decay to ε=0.01
```

### Softmax (Boltzmann) Exploration

```
P(a|s) = exp(Q(s,a)/τ) / Σa' exp(Q(s,a')/τ)

τ = temperature
High τ: More uniform (exploration)
Low τ: More greedy (exploitation)
```

## Practice Questions

**Short Answer (2 marks each)**

1. What is a Markov Decision Process? Name its components.
2. What is the Bellman equation for V*(s)?
3. What is the ε-greedy policy? Why is exploration important?
4. How does Q-learning differ from Dynamic Programming?

**Long Answer (8 marks each)**

1. Explain Q-learning algorithm in detail. Derive the Q-learning update rule.
2. Compare TD learning and Monte Carlo methods in terms of bias, variance and update frequency.
3. What is DQN? How does experience replay and target network improve stability?

**Think & Apply**

1. For the following MDP, calculate V*(s) for all states using value iteration (γ=0.9):

```
States: S1, S2, S3 (terminal)
Actions: a1, a2

From S1:
  a1: P(S2)=1, r=0
  a2: P(S3)=1, r=10

From S2:
  a1: P(S3)=1, r=5
  a2: P(S1)=1, r=-1

V(S3) = 0 (terminal)
```

2. An RL agent learning to play chess has a state space of 10⁴⁷. Why can't we use a simple Q-table? What alternative would you use?

[← Decision Trees](/courses/paiml/unit5/decision-trees/) | [Back to Course Overview →](/courses/paiml/)
