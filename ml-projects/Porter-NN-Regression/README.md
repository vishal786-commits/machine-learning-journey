# Porter — Delivery Time Prediction with Neural Networks

Predicting intra-city delivery times for **Porter** (India's largest last-mile
logistics marketplace) using a feed-forward neural network, on ~175K real
deliveries. The project covers the full pipeline: EDA, data cleaning, feature
engineering, model building, hyperparameter tuning, and interpretation.

> **The headline isn't the accuracy — it's the insight.** The most valuable
> finding is *why* deliveries run late: **fleet congestion, not trip distance.**
> More on that below.

---

## Key Result

| Metric | Value |
|---|---|
| Test R² | 0.996 |
| Test MAE | 0.44 min |
| Test RMSE | 0.57 min |
| Predictions within 2 min | 99.7% |

**An honest note on that R².** This number is unusually high because the dataset
ships with a **pre-filtered target** (delivery times cleaned to a narrow 32–110
minute band with no missing values). A near-deterministic target is easy to fit.
On raw, unfiltered production data, delivery-time R² for this problem typically
lands around **0.25–0.45** — a large share of variance (traffic, prep time,
driver behaviour) is irreducible. I report the real number *and* the caveat,
because a sub-minute error on delivery-time prediction should raise a question,
not just a cheer. Verifying it wasn't data leakage (via a held-out ablation) was
part of the work.

---

## The Core Insight: Congestion Beats Distance

A linear model reaches only R² 0.54 on this data; the neural network reaches
0.99. That gap is the whole story — **the signal is strongly non-linear**, and
permutation importance shows exactly where it lives:

| Feature | Importance (R² drop) | Linear correlation |
|---|---|---|
| `total_outstanding_orders` | **7.54** | 0.38 |
| `total_onshift_dashers` | **3.40** | 0.17 |
| `estimated_..._driving_duration` | 0.47 | 0.46 |
| `total_busy_dashers` | 0.36 | 0.21 |

The fleet-load features are **10–15× more important to the network than their
linear correlations suggest.** The model learned that delivery time responds
non-linearly to system load — staying stable until the fleet *saturates*, then
spiking. Trip distance, the strongest *linear* predictor, is only the third most
important feature to the network.

**A confounding caveat that keeps the recommendations honest:**
`total_onshift_dashers` correlates *positively* with delivery time (more partners
on shift → *longer* deliveries). This is **not causal** — Porter schedules more
partners *because* it anticipates high demand, so on-shift count is a proxy for
busyness, not a cause of delay. The defensible business lever is therefore
**reducing order backlog relative to available capacity**, not naively adding
headcount.

---

## Business Recommendations

- **Manage supply against backlog**, not raw headcount. Trigger surge incentives
  / batching limits when the backlog-to-capacity ratio approaches fleet
  saturation — *before* delivery times spike.
- **Deploy dynamic, load-aware ETAs** that reflect real-time congestion instead
  of static averages.
- **Prioritise congestion relief over route optimisation** — trip distance
  matters far less than fleet load.
- **Weight capacity planning toward temporal demand** (weekends and specific
  hours carry real signal).

---

## Pipeline

1. **EDA** — distributions, correlations, outlier detection (IQR), and the
   discovery that timestamps are UTC (which invalidated a naive "peak hour"
   feature — caught and removed).
2. **Cleaning** — dropped 90 rows with impossible negatives (negative prices /
   partner counts); no true duplicates.
3. **Feature engineering** — time features from `created_at`, fleet ratios, and
   grouping 73 store categories → 37 (rare categories bucketed into "Other").
4. **Preprocessing** — log-transform of skewed features, `total_items` capped at
   the 99th percentile, one-hot encoding, `StandardScaler` **fit on train only**
   (leakage-safe).
5. **Modelling** — Keras `Sequential` regressor (ReLU hidden layers, linear
   output, Adam, MSE loss, early stopping).
6. **Tuning** — Keras Tuner (Hyperband) over depth, width, dropout, learning
   rate. Finding: the model **doesn't overfit** — added depth and dropout
   slightly *hurt*, so the simpler baseline was kept.
7. **Interpretation** — permutation importance + directional analysis (above).

---

## Tech Stack

`Python` · `pandas` · `NumPy` · `scikit-learn` · `TensorFlow / Keras` ·
`Keras Tuner` · `Matplotlib` · `Seaborn`

---

## Dataset

~175,777 deliveries, 14 raw columns spanning order attributes (items, subtotal,
prices), store/market metadata, and **real-time fleet state** (on-shift / busy
partners, outstanding orders) at order time. The regression target,
`delivery_time`, is *derived*: `actual_delivery_time − created_at`, in minutes.

---

## Limitations & Honesty

- The high R² reflects a **pre-cleaned target**, not production-grade difficulty
  (explained above).
- Feature effects are **correlational, not causal** — the `total_onshift_dashers`
  confounding is the clearest example.
- The model is a black box; interpretation relies on permutation importance
  rather than direct coefficients.

---

## Author

Built as a data science case study on neural-network regression for logistics
ETA prediction.
