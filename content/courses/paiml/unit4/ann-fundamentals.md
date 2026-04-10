---
title: "4.1 Neural Networks Fundamentals"
date: 2026-02-01
description: "Perceptrons, multilayer networks, backpropagation algorithm with face recognition example for M.Tech PAIML."
categories: ["Courses"]
tags: ["neural-networks", "perceptron", "backpropagation", "multilayer", "mtech"]
_build:
  list: never
  render: always
---

## Biological Inspiration

Artificial Neural Networks (ANNs) are inspired by the human brain.

| Biological | Artificial |
|-----------|-----------|
| Neuron | Node/Unit |
| Dendrites | Input connections |
| Axon | Output |
| Synapse | Weight |
| Firing threshold | Activation function |

Human brain: ~10¹¹ neurons, each connected to ~10⁴ others.

## The Artificial Neuron (Perceptron)

A perceptron computes a weighted sum of inputs and applies an activation function.

```
Input: x = (x₁, x₂, ..., xₙ)
Weights: w = (w₁, w₂, ..., wₙ)
Bias: w₀

Net input: net = w₀ + Σ wᵢxᵢ = w·x + b

Output: y = f(net)
```

### Activation Functions

| Function | Formula | Range | Use |
|----------|---------|-------|-----|
| **Step** | 1 if net>0, else 0 | {0,1} | Binary classification |
| **Sigmoid** | 1/(1+e^(-net)) | (0,1) | Probability output |
| **Tanh** | (e^x - e^(-x))/(e^x + e^(-x)) | (-1,1) | Hidden layers |
| **ReLU** | max(0, net) | [0,∞) | Deep networks |
| **Softmax** | e^(xᵢ)/Σe^(xⱼ) | (0,1) | Multi-class output |

## Perceptron Learning

For linearly separable problems, the perceptron learning rule converges.

### Algorithm

```
Initialize weights w randomly (small values)

Repeat until convergence:
  For each training example (x, y_true):
    y_pred = step(w·x)
    if y_pred ≠ y_true:
      w ← w + η(y_true - y_pred)x
      
where η = learning rate (0 < η ≤ 1)
```

### Example — AND Gate

```
Training data:
x1  x2  | y
 0   0  | 0
 0   1  | 0
 1   0  | 0
 1   1  | 1

Initial weights: w=(0.5, 0.5), bias=0, η=0.1

Iteration 1: (0,0,0) → net=-0.5, pred=0, correct
Iteration 2: (0,1,0) → net=0.5, pred=1, WRONG
  w₀ ← 0 + 0.1×(0-1)×1 = -0.1 (bias update)
  w₁ ← 0.5 + 0.1×(0-1)×0 = 0.5
  w₂ ← 0.5 + 0.1×(0-1)×1 = 0.4
...
(Continue until convergence)
```

### Perceptron Convergence Theorem

If training data is linearly separable, the perceptron learning algorithm will converge to a correct solution in finite steps.

### Limitation: XOR Problem

Perceptron CANNOT solve XOR:
```
x1  x2  | XOR
 0   0  | 0
 0   1  | 1
 1   0  | 1
 1   1  | 0

No single line separates 0s from 1s → Need multilayer network
```

## Multilayer Networks

Adds hidden layers between input and output to solve non-linear problems.

### Architecture

```
Input Layer → Hidden Layer(s) → Output Layer

Example (3-2-1 network):
  x₁ ──┐
  x₂ ──┤── h₁ ──┐
  x₃ ──┤        ├── y
       └── h₂ ──┘
```

### Forward Pass

For each layer:
```
netⱼ = Σᵢ wᵢⱼ × aᵢ + bⱼ
aⱼ = f(netⱼ)

where:
  aᵢ = output of previous layer neuron i
  wᵢⱼ = weight from i to j
  f = activation function
```

## Backpropagation Algorithm

Backpropagation computes gradients of the loss with respect to all weights using the chain rule.

### Loss Function

**MSE for regression:**
```
L = (1/2) Σ (y_true - y_pred)²
```

**Cross-entropy for classification:**
```
L = -Σ y_true × log(y_pred)
```

### Algorithm

```
1. FORWARD PASS: Compute outputs layer by layer

2. COMPUTE OUTPUT ERROR:
   δₖ = (yₖ - oₖ) × f'(netₖ)    [output layer]

3. BACKPROPAGATE ERROR:
   δⱼ = f'(netⱼ) × Σₖ wⱼₖ × δₖ  [hidden layer]

4. UPDATE WEIGHTS:
   wᵢⱼ ← wᵢⱼ + η × δⱼ × aᵢ

5. REPEAT until convergence
```

### Detailed Example — XOR Network

**Network:** 2 inputs → 2 hidden (sigmoid) → 1 output (sigmoid)

```
Initial weights (example):
  w₁₁=0.5, w₂₁=0.5  (input→hidden1)
  w₁₂=-0.5, w₂₂=0.5 (input→hidden2)
  v₁=0.5, v₂=-0.5    (hidden→output)

Input: x=(1,0), target y=1

Forward pass:
  h1_net = 0.5×1 + 0.5×0 = 0.5
  h1_out = sigmoid(0.5) = 0.622
  
  h2_net = -0.5×1 + 0.5×0 = -0.5
  h2_out = sigmoid(-0.5) = 0.378
  
  out_net = 0.5×0.622 + (-0.5)×0.378 = 0.122
  out = sigmoid(0.122) = 0.530

Loss: L = 0.5×(1-0.530)² = 0.110

Backward pass:
  δ_out = (1-0.530) × 0.530×(1-0.530) = 0.117
  
  δ_h1 = 0.622×(1-0.622) × 0.5×0.117 = 0.014
  δ_h2 = 0.378×(1-0.378) × (-0.5)×0.117 = -0.014

Weight updates (η=0.1):
  v₁ ← 0.5 + 0.1×0.117×0.622 = 0.507
  v₂ ← -0.5 + 0.1×0.117×0.378 = -0.496
  w₁₁ ← 0.5 + 0.1×0.014×1 = 0.501
```

## Remarks on Backpropagation

**Strengths:**
- Works for any differentiable activation function
- Can learn complex non-linear functions
- Widely applicable

**Weaknesses:**
- Local minima — may not find global optimum
- Slow convergence for large networks
- Vanishing gradient problem in deep networks
- Sensitive to learning rate

**Improvements:**
- **Momentum:** Add fraction of previous update
- **Adaptive learning rates:** Adam, RMSProp
- **Batch normalization:** Normalize layer inputs
- **Dropout:** Randomly disable neurons during training

## Face Recognition Example

**Application:** Recognize person from 20×20 pixel face images.

```
Architecture:
  Input:    400 units (20×20 pixels, grayscale 0-1)
  Hidden:   3 hidden layers (200, 100, 50 units)
  Output:   1 unit per person (softmax)

Training:
  Dataset: 1000 face images, 20 people (50 each)
  Train/Test: 800/200

Results after training:
  Training accuracy: 98%
  Test accuracy: 94%
```

**Preprocessing:** Normalize pixel values, align faces.

## Practice Questions

**Short Answer (2 marks each)**

1. What is a perceptron? Draw its structure.
2. Why can't a single perceptron solve the XOR problem?
3. State the perceptron convergence theorem.
4. What is the vanishing gradient problem?

**Long Answer (8 marks each)**

1. Explain the backpropagation algorithm in detail. Derive the weight update rules for output and hidden layers.
2. What are the limitations of the perceptron? How do multilayer networks overcome them?
3. Explain backpropagation with a numerical example for a 2-2-1 network.

**Think & Apply**

1. A neural network for digit recognition has:
   - 784 input neurons (28×28 image)
   - 2 hidden layers with 256 and 128 neurons
   - 10 output neurons
   
   Calculate total number of weights in this network.

2. The gradient is vanishing in a deep network. What would you change: activation function, weight initialization, or architecture? Justify.

[← Unit 4 Overview](/courses/paiml/unit4/) | [Next: Advanced ANN →](/courses/paiml/unit4/advanced-ann/)
