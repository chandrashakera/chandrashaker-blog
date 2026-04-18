---
title: "4.2 Advanced Neural Networks — CNNs & Recurrent Networks"
date: 2026-02-01
sidebar: false
description: "Error functions, recurrent neural networks, convolutional neural networks for image processing - M.Tech PAIML Unit 4."
categories: ["Courses"]
tags: ["cnn", "rnn", "deep-learning", "convolutional", "recurrent", "mtech"]
build:
  list: never
  render: always
---

## Error Functions in Neural Networks

The error function (loss function) guides learning. Choice depends on the task.

### Regression Error Functions

**Mean Squared Error (MSE):**
```
L = (1/n) Σ (yᵢ - ŷᵢ)²

Gradient: ∂L/∂ŷ = -2(y - ŷ)
```

**Mean Absolute Error (MAE):**
```
L = (1/n) Σ |yᵢ - ŷᵢ|

More robust to outliers than MSE.
```

**Huber Loss:** Combines MSE and MAE — quadratic for small errors, linear for large errors.

### Classification Error Functions

**Binary Cross-Entropy:**
```
L = -[y×log(ŷ) + (1-y)×log(1-ŷ)]
```

**Categorical Cross-Entropy (multi-class):**
```
L = -Σₖ yₖ × log(ŷₖ)

where yₖ = 1 for true class, 0 otherwise
```

**Why Cross-Entropy over MSE for classification?**
- MSE has flat gradients near 0 and 1 → slow learning
- Cross-entropy has stronger gradients → faster learning

### Comparison

| Task | Loss Function | Output Activation |
|------|---------------|------------------|
| Binary classification | Binary cross-entropy | Sigmoid |
| Multi-class | Categorical cross-entropy | Softmax |
| Regression | MSE / MAE | Linear |
| Multi-label | Binary cross-entropy | Sigmoid per unit |

## Recurrent Neural Networks (RNN)

RNNs process **sequential data** by maintaining a hidden state across time steps.

### Why RNNs?

Standard neural networks:
- Fixed input size
- No memory of previous inputs

RNNs:
- Variable input length
- Hidden state carries information across time
- **"Memory"** of sequence history

### RNN Architecture

```
x₁ → [RNN] → h₁ → y₁
x₂ → [RNN] → h₂ → y₂
x₃ → [RNN] → h₃ → y₃

hₜ = f(Wₕhₜ₋₁ + Wₓxₜ + b)
yₜ = g(Wᵧhₜ)

where:
  hₜ = hidden state at time t
  xₜ = input at time t
  Wₕ = hidden-to-hidden weight matrix
  Wₓ = input-to-hidden weight matrix
```

### RNN Applications

| Application | Input | Output |
|-------------|-------|--------|
| Language modeling | Sequence of words | Next word |
| Sentiment analysis | Sentence | Positive/Negative |
| Machine translation | English sentence | French sentence |
| Speech recognition | Audio frames | Text |
| Time series | Historical values | Future values |

### Vanishing Gradient in RNNs

For long sequences, gradients vanish during backpropagation through time (BPTT):
```
∂L/∂h₁ = ∂L/∂hₜ × Π(∂hₜ/∂hₜ₋₁)

If ∂hₜ/∂hₜ₋₁ < 1 → product → 0 as t increases
```

**Solution: LSTM (Long Short-Term Memory)**

LSTM uses gates to control information flow:
```
Forget gate: fₜ = σ(Wf[hₜ₋₁, xₜ] + bf)
Input gate:  iₜ = σ(Wi[hₜ₋₁, xₜ] + bi)
Cell update: C̃ₜ = tanh(Wc[hₜ₋₁, xₜ] + bc)
Cell state:  Cₜ = fₜ⊙Cₜ₋₁ + iₜ⊙C̃ₜ
Output gate: oₜ = σ(Wo[hₜ₋₁, xₜ] + bo)
Hidden:      hₜ = oₜ⊙tanh(Cₜ)
```

## Convolutional Neural Networks (CNNs)

CNNs are specialized for **grid-like data** — images, audio, video.

### Why CNNs for Images?

**Problems with fully connected networks for images:**
- 1000×1000 image = 1,000,000 inputs
- Fully connected to 1000 hidden units = 10⁹ parameters!
- Doesn't exploit spatial structure

**CNN solutions:**
- **Local connectivity:** Each neuron connects to small region
- **Weight sharing:** Same filter applied across entire image
- **Pooling:** Reduces spatial dimensions

### CNN Building Blocks

#### 1. Convolutional Layer

Applies a **filter (kernel)** that slides over the input:

```
Input: 6×6 image
Filter: 3×3 kernel

        Input           Filter      Output (4×4)
    1 1 1 0 0 0       1 0 1       4 3 4 2
    0 0 1 1 1 0    ×  0 1 0  =    2 4 3 3
    0 0 0 1 1 0       1 0 1       2 3 4 1
    0 0 0 1 1 0                   ...
    0 0 1 1 0 0
    0 1 1 0 0 0

Each output value = dot product of filter with corresponding patch
```

**Key parameters:**
- **Filter size:** 3×3, 5×5, 7×7
- **Number of filters:** Depth of output (feature maps)
- **Stride:** Step size of filter movement
- **Padding:** 'valid' (no padding) or 'same' (zero padding)

**Output size:**
```
Output = (Input - Filter + 2×Padding) / Stride + 1
```

#### 2. ReLU Activation

Applied after each convolution to add non-linearity:
```
f(x) = max(0, x)
```

#### 3. Pooling Layer

Reduces spatial dimensions, provides translation invariance.

**Max Pooling (2×2, stride=2):**
```
4 3 2 1       4 2
2 5 1 2  →    6 3
9 6 8 2       9 8
4 3 2 1       4 2

Takes maximum value in each 2×2 region.
```

**Average Pooling:** Takes average instead of maximum.

#### 4. Fully Connected Layer

At the end, flatten feature maps and connect to output:
```
Feature maps → Flatten → Dense layer → Softmax → Class probabilities
```

### CNN Architecture Example — LeNet-5

Classic CNN for digit recognition (LeCun, 1998):

```
Input (32×32×1)
    ↓
Conv1: 6 filters, 5×5 → (28×28×6)
    ↓
MaxPool: 2×2 → (14×14×6)
    ↓
Conv2: 16 filters, 5×5 → (10×10×16)
    ↓
MaxPool: 2×2 → (5×5×16)
    ↓
Flatten → 400 units
    ↓
FC: 120 units
    ↓
FC: 84 units
    ↓
Output: 10 units (Softmax)
```

**Parameters:**
- Conv1: 6 × (5×5×1 + 1) = 156
- Conv2: 16 × (5×5×6 + 1) = 2,416
- FC layers: 48,120 + 10,164 + 850 = 59,134
- **Total: ~61,706** (vs millions for fully connected)

### Modern CNN Architectures

| Architecture | Year | Key Innovation |
|-------------|------|----------------|
| LeNet-5 | 1998 | First successful CNN |
| AlexNet | 2012 | Deep CNN, ReLU, Dropout |
| VGGNet | 2014 | Very deep (16-19 layers), 3×3 filters |
| GoogLeNet | 2014 | Inception modules |
| ResNet | 2015 | Skip connections, 152 layers |
| EfficientNet | 2019 | Compound scaling |

### What CNNs Learn

```
Early layers:  Detect edges, colors, textures
Middle layers: Detect shapes, parts (eyes, wheels)
Later layers:  Detect high-level features (faces, cars)
```

This **hierarchical feature learning** is why CNNs work so well for images.

## Practice Questions

**Short Answer (2 marks each)**

1. What is the difference between MSE and cross-entropy loss?
2. What is the vanishing gradient problem in RNNs? How does LSTM solve it?
3. What is weight sharing in CNNs? Why is it useful?
4. What does max pooling do? What property does it provide?

**Long Answer (8 marks each)**

1. Explain the architecture of a CNN. Describe each layer type with its purpose and mathematical operation.
2. Compare RNN and LSTM. Why are LSTMs preferred for long sequences?
3. Explain the LeNet-5 architecture. Calculate the output dimensions after each layer.

**Think & Apply**

1. An input image is 224×224×3 (RGB). A convolutional layer has 64 filters of size 3×3, stride=1, padding='same'. Calculate:
   - Output dimensions
   - Number of parameters in this layer

2. For a sentiment analysis task (positive/negative), design an RNN architecture. What loss function would you use? What activation at output?

[← ANN Fundamentals](/courses/paiml/unit4/ann-fundamentals/) | [Next: Unit 5 →](/courses/paiml/unit5/)
