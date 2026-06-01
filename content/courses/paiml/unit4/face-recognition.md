---
title: "An Example: Face Recognition Using Backpropagation"
date: 2026-06-01
description: "A complete walkthrough of applying Backpropagation to face recognition — input encoding, output encoding, network structure, training parameters, and the learned hidden representations. Based on Mitchell Chapter 4, Section 4.7."
tags: ["paiml", "unit4", "backpropagation", "face-recognition", "neural-networks", "design-choices"]
categories: ["courses", "paiml"]
math: true
weight: 6
---

## Unit 4 Navigation

**← [Remarks on Backpropagation](/courses/paiml/unit4/remarks-backpropagation/)**
&nbsp;|&nbsp;
**Next → [Advanced Topics: Error Functions](/courses/paiml/unit4/advanced-error-functions/)**

---

## 4.7 Face Recognition with Backpropagation

This section walks through applying Backpropagation to a real learning task — recognising which direction a person is facing from a camera image. It illustrates the **design decisions** every ANN practitioner must make, and what the network actually learns internally.

---

## 4.7.1 The Task

### Dataset

| Property | Detail |
|----------|--------|
| Total images | 624 greyscale images |
| Subjects | 20 different people |
| Images per person | ~32 |
| Image resolution | 120 × 128 pixels |
| Pixel depth | Greyscale, 0–255 |

**Variations within the dataset:**
- **Expression:** happy, sad, angry, neutral
- **Direction:** left, right, straight ahead, up
- **Accessories:** sunglasses or not
- **Background:** varies per person
- **Head position:** varies within frame

### Classification Target

**Task selected:** Predict the **direction the person is facing** — one of four classes:
- Looking left
- Looking right
- Looking straight ahead
- Looking up

*Other possible targets from the same dataset: identity, gender, expression, wearing sunglasses — all learnable to high accuracy.*

---

## 4.7.2 Design Choices

Every ANN application requires decisions about representation, architecture, and training. Below are the choices made for this task.

---

### Design Choice 1: Input Encoding

**Problem:** The full image is 120 × 128 = 15,360 pixels — too many weights for efficient training.

**Solution:** Downsample to a **30 × 32 coarse image** (960 pixels):
- Each coarse pixel = mean intensity of the corresponding region in the full image
- Provides sufficient resolution for face direction classification
- Manageable number of weights

**Scaling:** Pixel values 0–255 are scaled to **[0, 1]** to match the output range of sigmoid units.

**Comparison to ALVINN:** ALVINN uses the same idea but samples one random pixel per region instead of averaging — faster computation for real-time driving, at some cost in quality.

---

### Design Choice 2: Output Encoding

**1-of-4 (one-hot) encoding** for the four face directions:

| Direction | Output vector |
|-----------|---------------|
| Looking left | (high, low, low, low) |
| Looking straight | (low, high, low, low) |
| Looking right | (low, low, high, low) |
| Looking up | (low, low, low, high) |

**Why 1-of-4, not a single unit with values 0.25/0.50/0.75/1.0?**

1. **More weights available** at the output layer — 4× more parameters for distinguishing the classes
2. **Confidence measurement:** The gap between the highest-valued output and the second-highest indicates prediction confidence. Near-ties signal ambiguous classifications.

---

### Design Choice 3: Target Values — 0.1 and 0.9 Instead of 0 and 1

The sigmoid function approaches 0 and 1 **only asymptotically** — it never exactly reaches these values with finite weights. If we use target values of 0 and 1:

- Gradient descent forces weights to grow **without bound** trying to reach the unachievable targets
- Training never converges

**Solution:** Use target values of **0.1** (instead of 0) and **0.9** (instead of 1).

```
Target for "looking left":   (0.9, 0.1, 0.1, 0.1)
Target for "looking right":  (0.1, 0.1, 0.9, 0.1)
```

These values are **achievable** by a sigmoid unit with finite weights.

---

### Design Choice 4: Network Structure

**Architecture chosen:** 960 inputs → **3 hidden units** → 4 output units

| Design question | Decision | Rationale |
|-----------------|----------|-----------|
| Number of hidden layers | 1 | One or two sigmoid layers can approximate any function; more layers increase training time |
| Number of hidden units | 3 | Achieves 90% accuracy; sufficient for this task |
| Layer type | Sigmoid + linear output | Standard for classification |

**Experiment with 30 hidden units:**
- Accuracy: ~91–92% (1–2% better)
- Training time: ~1 hour vs. ~5 minutes for 3 hidden units
- Conclusion: diminishing returns from more hidden units when using cross-validation

**General principle:** With cross-validation, extra hidden units typically increase overfitting risk rather than generalisation accuracy. The minimum number needed for the task is often best.

---

### Design Choice 5: Training Parameters

| Parameter | Value | Notes |
|-----------|-------|-------|
| Learning rate η | 0.3 | Lower values work but slower; too high fails to converge |
| Momentum α | 0.3 | Consistent convergence improvement |
| Weight initialisation | Output units: small random; Input unit weights: 0 | Zero input weights give more interpretable visualisations |
| Training examples | 260 images | Remaining used for validation and test |
| Gradient descent type | Full batch | Entire training set used before each update |

---

### Design Choice 6: Stopping Criterion

The validation-based procedure from [Section 4.6.5](/courses/paiml/unit4/remarks-backpropagation/#465-generalisation-overfitting-and-stopping-criterion):

1. Evaluate on the validation set every 50 gradient descent steps
2. Keep the network with the **highest validation set accuracy**
3. Report accuracy on a **third test set** never used during training

This three-way split — training / validation / test — ensures the reported accuracy is a genuine measure of generalisation.

---

## 4.7.3 Results

| Metric | Value |
|--------|-------|
| Training images | 260 |
| Test accuracy (3 hidden units) | **90%** |
| Baseline (random guess) | 25% |
| Training time (3 hidden) | ~5 minutes (Sun Sparc5) |
| Training time (30 hidden) | ~1 hour |

A **3.6× improvement** over random guessing, using only 3 hidden units connecting 960 pixel inputs to 4 output classes.

---

## 4.7.4 Learned Hidden Representations

### What the Network Learned

After 100 training iterations, the hidden unit weights are inspected by plotting the 30×32 weight matrix at the position of each corresponding input pixel.

**Observable pattern:** The weights concentrate in the region of the image where faces typically appear — the network learns to **focus attention on the face and body area**, ignoring background.

**Example — "Looking right" output unit:**
- Strong positive weight from hidden unit 2
- Strong negative weight from hidden unit 3
- Hidden unit 2's weights: large positive values where a rightward-facing face's bright skin appears
- Hidden unit 3's weights: the inverse pattern
- Together: the two hidden units detect the contrast between a face turned right vs. not

### Evolution of Weights During Training

**After 1 iteration:** Weights are near-random, roughly uniform — no structure visible.

**After 100 iterations:** Weights organise into face-sensitive patterns. The network has learned which pixel regions carry information about head direction.

This illustrates the key ANN property: **internal feature discovery**. The designer provided only raw pixels and direction labels; the hidden units independently discovered that facial position and orientation patterns are the relevant features.

---

## Complete Design Summary

```
Dataset:        624 greyscale images, 20 people, 4 directions
Input:          30×32 pixels, scaled to [0,1]   → 960 input units
Hidden layer:   3 sigmoid units
Output layer:   4 units (one per direction)
Target values:  0.9 (target class) / 0.1 (other classes)
Learning rate:  η = 0.3
Momentum:       α = 0.3
Training set:   260 images
Test accuracy:  90%  (vs. 25% chance)
```

---

## Lessons from This Example

1. **Input preprocessing matters** — downsampling and scaling improve both training speed and final accuracy
2. **1-of-n output encoding** is preferred for multi-class classification over single-unit encoding
3. **Target values of 0.1/0.9 not 0/1** — critical to avoid unbounded weight growth
4. **More hidden units ≠ better generalisation** — cross-validation determines the appropriate network size
5. **Validation-based stopping** is essential — training error alone is a misleading stopping criterion
6. **Hidden layers learn features automatically** — the designer need not specify what the intermediate representations should be

---

## Practice Questions

1. Why are pixel values rescaled to [0, 1] before being fed to the network?
2. Explain two advantages of 1-of-4 output encoding over a single output unit for 4-way classification.
3. Why must target values be 0.1 and 0.9 instead of 0 and 1? What happens if you use 0 and 1?
4. In the face recognition experiment, what did the hidden unit weights look like after 100 iterations? What does this tell us about how ANNs learn?
5. The 30-hidden-unit network achieved 1–2% higher accuracy than the 3-unit network. Should you always use the larger network? Why or why not?

---

## References

- Mitchell, T.M. — *Machine Learning*, Chapter 4, Section 4.7 &nbsp; [📄 PDF](https://www.cim.mcgill.ca/~jer/courses/ai/readings/MitchellCh4.pdf)
- Cottrell, G.W. (1990) — *Extracting Features from Faces Using Compression Networks*

---

**← [Remarks on Backpropagation](/courses/paiml/unit4/remarks-backpropagation/)**
&nbsp;|&nbsp;
**Next → [Advanced Topics: Error Functions](/courses/paiml/unit4/advanced-error-functions/)**
