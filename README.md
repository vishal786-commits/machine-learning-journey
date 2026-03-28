# Machine Learning Journey

A structured, public record of building ML/AI engineering skills from the ground up — mathematical foundations first, production systems second.

This isn't a course repo or a collection of tutorials. Every notebook is written to understand *why* something works before reaching for a library that does it automatically.

---

## Repository Structure

| Repository | Focus | Status |
|---|---|---|
| [classical-ml](./classical-ml) | Core algorithms from scratch — Linear Regression, Logistic Regression, Decision Trees, kNN | 🟢 Active |
| Deep Learning *(coming soon)* | Neural networks, backpropagation, CNNs — NumPy first, then PyTorch | 🔵 Planned |
| Production AI Systems *(coming soon)* | RAG pipelines, LLM applications, agentic systems | 🔵 Planned |

---

## Approach

Each topic follows the same progression:

1. **Understand the math** — derive equations before writing a single line of code
2. **Implement from scratch** — NumPy only, no sklearn, no shortcuts
3. **Experiment on real data** — evaluate, visualise, and stress-test
4. **Analyse trade-offs** — interpret *why* results look the way they do

The goal is not just working code. It's the ability to reason about what happens when things break.

---

## The Bigger Picture

This repository is the foundation layer of a longer roadmap:

```
Classical ML (this repo)
        ↓
Deep Learning & Neural Networks
        ↓
LLMs, Transformers, Embeddings
        ↓
Production AI Systems — RAG, Agents, MLOps
```

Understanding gradient descent here makes backpropagation there intuitive.  
Understanding decision boundaries here makes attention mechanisms there less abstract.

---

## Current Progress

- [x] Linear Regression
- [x] Logistic Regression (Binary)
- [x] Logistic Regression (Multiclass — One-vs-Rest)
- [x] k-Nearest Neighbours (kNN)
- [x] Decision Tree (Classification & Regression)
- [ ] Support Vector Machines
- [ ] Naive Bayes
- [ ] Ensemble Methods (Random Forest, Gradient Boosting)
- [ ] Neural Networks from scratch

---

## License

MIT
