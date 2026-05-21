# FiTech — Data-Driven Credit Card Product Design

> A two-stage test-and-rollout campaign strategy to maximize profitability for a fintech email solicitation targeting 750K customers — matching 12 credit card products to 3 credit risk segments using CLV modeling and experimental design.

---

## Overview

FiTech needs to maximize profitability from an email solicitation campaign targeting 750,000 customers segmented by bankruptcy (BK) scores. With 12 credit card products varying in APR, annual fee, and rate type, the challenge is to match the right product to the right risk segment — and design a two-round test-and-rollout experiment to learn efficiently while maximizing expected profit.

---

## The Problem

| Parameter | Value |
|---|---|
| Customers targeted | 750,000 |
| Credit card products | 12 (varying APR, annual fee, rate type) |
| Customer segments | 3 (BK scores: 150, 200, 250) |
| Campaign rounds | 2 (test → rollout) |

---

## CLV Driver Analysis

| Driver | Impact | Example |
|---|---|---|
| BK Score | ↑ BK → ↓ CLV | BK 150: $83 → BK 200: $63 → BK 250: $33 (Product #1) |
| APR | ↑ APR → ↑ CLV | ~+$10 CLV per +1% APR |
| Annual Fee | Fee → ↑ CLV | $20 fee adds ~$30 to CLV |
| Rate Type | Variable → ↑ CLV | +$10 CLV consistently vs fixed |

---

## Experiment Design

### Round 1 — Test
- **Full factorial**: 36 trials (12 products × 3 segments)
- **Partial factorial chosen**: 12 trials
- **Design efficiency**: 0.892
- **Sample size**: 3,789 customers
- **Emails saved**: 90,936
- **Cost saved**: $81,068

### Round 2 — Rollout
- Used average CLV from historical data + Round 1 test results
- Allocated emails using CLV-weighted proportions per segment
- Matched best product to each BK risk tier

---

## Modeling Approach

### Logistic Regression
- Predicts P(response) per product-segment combination
- Used with and without interaction terms
- Combined with CLV estimates to compute expected profit per offer

### Expected Profit Framework
```
Expected Profit per customer = P(response) × CLV(product, BK_score)

Target: send offer only when Expected Profit > 0
```

---

## Key Results

- Personalized offer matching outperformed random and uniform strategies
- Partial factorial design saved $81,068 vs full factorial
- Round 2 rollout optimized allocation using CLV-weighted proportions

---

## Project Structure

```
fitech-credit-card/
├── fitech_analysis.ipynb     ← Full analysis (EDA, CLV modeling, experiment design)
├── README.md
└── LICENSE
```

---

## Tech Stack

| Tool | Purpose |
|---|---|
| **Python** | Data analysis, CLV modeling, experiment design |
| **Logistic Regression** | Response propensity modeling per product-segment |
| **CLV Modeling** | Customer lifetime value by BK score, APR, fee, rate type |
| **Experimental Design** | Partial factorial with 89.2% efficiency |
| **Pandas / NumPy** | Data manipulation and allocation logic |
| **Simulation Tool** | Scenario analysis for expected profit estimation |

---

## Author

**Krithika Suwarna**
[LinkedIn](https://linkedin.com/in/krithika-suwarna) · [Portfolio](https://krithikasuwarna.com) · [Slides](https://docs.google.com/presentation/d/1f_0S7WBNyJkQXIBJjQLZR2-OrFKGUej_t_6_KzqJAio/edit?slide=id.g33fa2843bcc_0_0#slide=id.g33fa2843bcc_0_0)
