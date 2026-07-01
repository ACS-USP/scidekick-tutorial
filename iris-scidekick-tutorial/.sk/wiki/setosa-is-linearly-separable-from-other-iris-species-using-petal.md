---
{title: Setosa is linearly separable from other Iris species using petal features alone,type: hypothesis,created: 2026-07-01T12:35:35.868Z,updated: 2026-07-01T12:35:35.869Z,tags: [],status: proposed}
---

# Hypothesis: Setosa is linearly separable from other Iris species using petal features alone

## Statement

A linear decision boundary using only petal length and petal width perfectly separates Iris setosa from the other two species (versicolor and virginica combined), with zero classification error.

## Rationale

EDA on the Iris dataset revealed zero range overlap between setosa and the other species in both petal features: setosa petal length [1.00, 1.90] vs versicolor [3.00, 5.10] and virginica [4.50, 6.90]; petal width [0.10, 0.60] vs [1.00, 1.80] and [1.40, 2.50]. This is a stronger claim than the original "all species are separable" hypothesis — it is narrower and directly supported by the data.

## Predictions

- If true: a linear classifier (e.g., logistic regression, linear SVM) trained on petal length and width achieves 100% accuracy in a one-vs-rest (setosa vs others) binary task, verified by cross-validation.
- If false: at least one setosa sample is misclassified, or a linear boundary cannot be drawn in the 2D petal space without errors.

## Experimental Approach

- [[iris-exploratory-data-analysis|Iris exploratory data analysis]] (provides supporting range analysis)
- Train/evaluate a linear classifier on petal features with cross-validation (planned)

## Evidence

- EDA range analysis: setosa petal length [1.00, 1.90] has zero overlap with versicolor [3.00, 5.10] or virginica [4.50, 6.90]. Same for petal width.
- Experiment: [[iris-exploratory-data-analysis|Iris exploratory data analysis]]

## Status

Status: **proposed** — supported by EDA range analysis; awaiting formal classifier validation.
