# Classical Machine Learning — From First Principles

> *"Modern ML frameworks abstract away complexity. This repository rebuilds it."*

A structured collection of classical ML algorithms implemented from scratch. Built to develop deep, system-level intuition about how models actually work before reaching for high-level libraries.

---

## Why From Scratch?

Every model in a framework hides the mechanics that matter most:

$$\mathcal{L}(\text{model}) = f(\text{Data},\ \text{Objective},\ \text{Optimization})$$

By deriving and implementing each component manually, you build:
- **Strong intuition** — you understand *why* a model behaves the way it does
- **Debugging ability** — you can reason about failures at the algorithmic level
- **Real-world readiness** — deeper understanding of production ML systems

---

## Approach

Each algorithm follows a consistent five-stage framework:

| Stage | What it covers |
|---|---|
| **Conceptual Intuition** | Geometric and statistical reasoning behind the algorithm |
| **Mathematical Formulation** | Deriving core equations and objective functions |
| **From-Scratch Implementation** | Python + NumPy only — no high-level ML libraries |
| **Experiments** | Evaluating behaviour on real datasets |
| **Analysis** | Interpreting results, trade-offs, and limitations |

---

## Implemented

- [x] Linear Regression
- [x] Logistic Regression
- [x] Multiclass Logistic Regression
- [x] k-Nearest Neighbours (kNN)
- [x] Decision Tree (Classification & Regression)

---

## Key Concepts Covered

- Bias–Variance Tradeoff
- Overfitting vs Underfitting
- Entropy and Gini Impurity
- Feature Importance
- Handling Numerical / Categorical Data
- Model Interpretability

---

## Upcoming

- [ ] Support Vector Machines (SVM)
- [ ] Naive Bayes
- [ ] Ensemble Methods
  - [ ] Random Forest
  - [ ] Gradient Boosting

---

## Broader Context

This repository is one layer in a deliberately structured ML/AI engineering journey. It serves as the mathematical foundation for:

- **Deep Learning** — understanding gradient flow, activations, and backprop from first principles
- **Large Language Models** — attention mechanisms, tokenisation, and transformer internals
- **RAG Systems** — retrieval, reranking, and generation pipelines built on solid ML intuition

---

## Philosophy

- Favour implementation details over API convenience  
- Build from first principles before optimising  
- Understand before you abstract  
- Learn by doing — always

---

## Tech Stack

`Python` · `NumPy` · `Jupyter Notebooks` · `Matplotlib`

---

*Part of the [machine-learning-journey](https://github.com/vishal786-commits) series.*
