# Pairwise Classification in Sports Prediction (March Madness)

## What is a Pairwise Classification Problem?

A pairwise classification problem is a machine learning setup where the model predicts the outcome between **two entities**.

Instead of predicting a property of a single object, the model predicts the relationship between two objects.

In the context of March Madness:

> Predict the probability that Team A beats Team B.

---

## Why This Is Different from Normal Classification

### Standard Classification Example

Input:
- Customer income
- Credit score
- Employment length

Output:
- Default (1) or Not Default (0)

---

### Pairwise Classification Example (Basketball)

Input:
- Team A statistics
- Team B statistics

Output:
- 1 if Team A wins
- 0 if Team B wins

The prediction is **relative**, not absolute.

---

## Why Sports Prediction Is Naturally Pairwise

Basketball games are comparative.

It is not:
> Is Team A strong?

It is:
> Is Team A stronger than Team B?

Team strength only matters relative to the opponent.

---

## Feature Engineering for Pairwise Modeling

For each historical game, we construct difference-based features.

Example:

| Metric | Team A | Team B |
|--------|--------|--------|
| Offensive Efficiency | 115 | 105 |
| Defensive Efficiency | 95 | 100 |
| Seed | 3 | 10 |

We create:

```text
OffEff_Diff = 115 - 105 = +10
DefEff_Diff = 95 - 100 = -5
Seed_Diff   = 3 - 10   = -7

Target:

```text
1 if Team A won
0 if Team B won

The model learns how differences in efficiency, defense, and seed translate into win probability.

# Mathematical Intuition

If:

Strength_A = 85
Strength_B = 78

We model:

P(A beats B) = sigmoid(Strength_A - Strength_B)

This difference modeling is the core idea of pairwise learning.

Why Difference Features Work Well

Using:

Feature_A - Feature_B

Instead of raw values:

Captures relative strength

Removes scale bias

Improves generalization

Makes the model symmetric

Avoiding Bias (Important Trick)

If we always assign:

Team1 = lower TeamID

Team2 = higher TeamID

The model may learn artificial ordering bias.

To prevent this:


