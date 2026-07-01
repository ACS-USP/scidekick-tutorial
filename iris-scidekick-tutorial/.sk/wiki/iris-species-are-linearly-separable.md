---
{title: Iris species are linearly separable.,type: hypothesis,created: 2026-07-01T12:18:00.446Z,updated: 2026-07-01T12:18:00.448Z,tags: [],status: rejected}
---

# Hypothesis: Iris species are linearly separable.

## Statement

The three Iris species (setosa, versicolor, virginica) are linearly separable — i.e., there exists a linear decision boundary that perfectly classifies all 150 samples in the 4-dimensional feature space.

## Rationale

Iris is a classic benchmark dataset. Fisher's original 1936 paper introduced linear discriminant analysis on it. The petal features are known to separate setosa cleanly, but versicolor and virginica overlap.

## Predictions

- If true: all three species clusters are disjoint and separable by hyperplanes in (a subset of) the 4D feature space.
- If false: at least one species pair cannot be perfectly separated by any linear boundary.

## Experimental Approach

- [[iris-exploratory-data-analysis|Iris exploratory data analysis]]

## Evidence
- EDA shows setosa is linearly separable from both versicolor and virginica via petal features (no overlap). However, versicolor and virginica overlap in petal length [4.50, 5.10] and petal width [1.40, 1.80]. The hypothesis is **rejected** — not all Iris species are linearly separable.

- Experiment: [[iris-exploratory-data-analysis|Iris exploratory data analysis]]

## Status

Status: **rejected** — versicolor and virginica are not linearly separable.

<!-- Status flow: draft → proposed → testing → confirmed | rejected -->
