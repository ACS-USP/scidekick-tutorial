---
{title: Petal dimensions alone discriminate Iris species,type: hypothesis,created: 2026-07-01T12:39:02.621Z,updated: 2026-07-01T12:39:02.622Z,tags: [],status: proposed}
---

# Hypothesis: Petal dimensions alone discriminate Iris species

## Statement

Petal length and petal width alone are sufficient to discriminate all three Iris species with high accuracy, using a linear model.

## Rationale

EDA shows that petal features carry the strongest class signal: setosa is perfectly separated from the other two (zero overlap in both petal features). Versicolor and virginica overlap partially — petal length [4.50, 5.10] and petal width [1.40, 1.80] — but the overlap zone contains only ~37-38 of 150 samples. Sepal features, by contrast, show heavy overlap across all species pairs. Petal dimensions are the dominant discriminative features.

## Predictions

- Logistic regression trained on petal length and petal width alone achieves >95% accuracy on the full 3-class Iris classification task, measured via stratified 5-fold cross-validation.

## Experimental Approach

- [[iris-exploratory-data-analysis|Iris exploratory data analysis]] (range analysis quantifying overlap)
- Train logistic regression on petal features with cross-validation (planned)

## Evidence

- EDA range analysis: setosa zero overlap with others; versicolor/virginica overlap is partial (~25% of those two classes).
- Experiment: [[iris-exploratory-data-analysis|Iris exploratory data analysis]]

## Status

Status: **proposed** — awaiting logistic regression validation.
