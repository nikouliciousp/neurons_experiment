# 🧠 Neurons Experiment
### From Plato to Transformers: Additive vs Divisive vs Hybrid Neurons

[![Live Demo](https://img.shields.io/badge/🚀_Live_Demo-GitHub_Pages-00d4ff?style=for-the-badge)](https://nikouliciousp.github.io/neurons_experiment/)
[![Language](https://img.shields.io/badge/Language-GR_/_EN-7c3aed?style=for-the-badge)](#)
[![MSc AI](https://img.shields.io/badge/MSc_AI-University_of_Essex-ff6b35?style=for-the-badge)](#)
[![License](https://img.shields.io/badge/License-MIT-10b981?style=for-the-badge)](LICENSE)

> *"Knowledge arises from the division of genus into species."* — Plato, Sophist

---

## 🎓 Academic Context

This project was developed by **Perikles Nikoules** as part of his **MSc in Artificial Intelligence at the University of Essex**. It originated as a conceptual exploration during coursework on neural network architectures — specifically while studying activation functions, forward propagation, and backpropagation.

The central question that motivated this work:

> **If ancient philosophers argued that thought is a continuous whole and reason divides it into categories — can the same logic apply to how neurons process information? Could a divisive operation be architecturally more expressive than a weighted sum?**

This led to a comparative empirical experiment between three neuron formulations, grounded in both the history of philosophy and published neuroscience.

---

## 🔬 Overview

An **interactive, standalone machine learning experiment** that bridges ancient philosophy and modern AI. Three neuron types — Additive, Divisive, and Hybrid — are trained simultaneously on the same dataset, with live visualisation of decision boundaries and loss curves.

**Fully bilingual** 🇬🇷 Greek / 🇬🇧 English — toggle in the top right corner.  
**Zero dependencies** — one HTML file, runs offline in any browser.  
**Mobile responsive** — works on any screen size.

---

## 💡 The Philosophical Hypothesis

| Philosopher | Concept | ML Equivalent |
|---|---|---|
| **Aristotle** | Synthesis — the whole is greater than the sum of its parts | **Additive Neuron**: z = Σ wᵢxᵢ + b |
| **Plato** | Diaeresis — knowledge through division of genus into species | **Divisive Neuron**: z = Σw⁺\|xᵢ\| / Σw⁻\|xᵢ\| |
| **Leibniz** | Logos — reason encompasses both synthesis and analysis | **Hybrid Neuron**: 0.5·Additive + 0.5·Divisive |
| **Biology** | Carandini & Heeger (2012) — visual cortex uses divisive normalisation | **Div. Norm.**: r = σxⁿ / (σ⁵⁰ + Σxⁿ) |

The key insight: the **Attention Mechanism** powering every modern Transformer (GPT, BERT, Claude) is mathematically a form of divisive normalisation:

```
Attention(Q, K, V) = softmax(QKᵀ / √d) · V
```

Plato's Diaeresis — in computational form, 2,400 years later.

---

## ⚡ Features

- **Live Training** — 3 neuron types train simultaneously, step by step or continuous auto mode
- **Decision Boundary Visualisation** — real-time colour-coded 2D canvas per neuron
- **Loss Curve Comparison** — live chart overlaying all three networks with value labels
- **Accuracy %** — live accuracy displayed alongside loss for each network
- **Winner highlight** — winning network glows with its colour in real time
- **Status bar** — explains what is happening at each epoch during training
- **Step-by-step guide** — numbered instructions for first-time visitors
- **4 Datasets** — XOR, Circle (radial), Spiral ✨ (hardest), Linear (simple)
- **Mathematics Tab** — full formulas, numerical examples, backpropagation derivatives for all 3 neurons
- **Philosophy Tab** — Aristotle, Plato, Leibniz, neuroscience, comparative table
- **Bilingual** 🇬🇷 / 🇬🇧 — all text switches instantly without page reload
- **Mobile responsive** — single-column layout on small screens
- **Zero dependencies** — pure HTML/CSS/JS, no npm, no build step, no internet required

---

## 🚀 Quick Start

### Option 1 — Open directly (no install)
Download `neurons_experiment.html` and open it in any browser. That is it.

### Option 2 — GitHub Pages (live link)
```
https://nikouliciousp.github.io/neurons_experiment/
```

### Option 3 — Clone and run locally
```bash
git clone https://github.com/nikouliciousp/neurons-experiment.git
cd neurons-experiment
open neurons_experiment.html       # macOS
start neurons_experiment.html      # Windows
xdg-open neurons_experiment.html   # Linux
```

---

## 🕹 How to Use

1. **Choose a dataset** — XOR, Circle, Spiral, or Linear
2. **Press AUTO** to start training, or use **+20 / +100** for manual steps
3. Watch the **Decision Boundaries** update live — the colour background shows where each network predicts class 1 vs class 0
4. Compare **Loss** (lower = better) and **Accuracy %** across the three networks
5. The **winner glows** — its card lights up when it achieves the lowest loss
6. Switch to **Mathematics** tab to understand the formulas, or **Philosophy** tab for the conceptual background

---

## 📐 Neuron Mathematics

### Additive Neuron — Aristotelian Synthesis
```
z = w₁x₁ + w₂x₂ + b
ŷ = σ(z)

Backprop:  ∂L/∂w₁ = (ŷ − y) · σ'(z) · x₁   (stable, analytical)
```

### Divisive Neuron — Platonic Diaeresis
```
num = w₁⁺·|x₁| + w₂⁺·|x₂|
den = w₁⁻·|x₁| + w₂⁻·|x₂| + ε
z   = num / den
ŷ   = σ(z)

Backprop:  ∂z/∂wP₁ = |x₁| / den
           ∂z/∂wN₁ = −num · |x₁| / den²
```

### Hybrid Neuron — Leibnizian Logos
```
z_add = w₁·x₁ + w₂·x₂ + b
z_div = num / den
z     = 0.5 · z_add + 0.5 · z_div
ŷ     = σ(z)

Backprop: both branches update simultaneously with chain rule
```

---

## 🧪 Experiment Results

| Dataset | Best Performer | Reason |
|---|---|---|
| **XOR** | Divisive / Hybrid | Non-linear structure benefits from ratio-based separation |
| **Circle** | Divisive | Radial symmetry maps naturally to divisive normalisation |
| **Spiral** | Divisive / Hybrid | Most complex — requires multiple non-linear cuts |
| **Linear** | Additive | Simple boundary; divisive complexity is unnecessary |

> Note: results vary slightly between runs due to random weight initialisation. Press ↺ Reset and re-run to see the general trend.

---

## 🏛 Scientific Background

- **Carandini & Heeger (2012)** — *Normalization as a canonical neural computation*, Nature Reviews Neuroscience. Empirical documentation of divisive normalisation in the mammalian visual cortex.
- **Vaswani et al. (2017)** — *Attention Is All You Need*. Introduction of the Transformer; attention as scaled dot-product division.
- **Hochreiter & Schmidhuber (1997)** — *Long Short-Term Memory*. Gating mechanisms as multiplicative operations over cell state.

---

## 📁 Repository Structure

```
neurons-experiment/
│
├── neurons_experiment.html   # Complete app — bilingual, responsive, zero dependencies
└── README.md                 # This file
```

---

## 📄 License

MIT License — free to use, modify, and distribute with attribution.

---

<div align="center">

*"The whole is more than the sum of its parts."* — Aristotle

*"Knowledge arises from the division of genus into species."* — Plato

**Both were right. Modern AI uses both.**

*Developed during MSc AI studies — University of Essex*

</div>
