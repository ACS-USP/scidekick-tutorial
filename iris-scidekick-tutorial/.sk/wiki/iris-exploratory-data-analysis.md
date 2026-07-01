---
{title: Iris exploratory data analysis,type: experiment,created: 2026-07-01T12:22:57.216Z,updated: 2026-07-01T12:22:57.217Z,tags: [],base_protocol: ""}
---

# Experiment: Iris exploratory data analysis

## Base Protocol

Load Iris dataset (150 samples, 3 species × 50 each, 4 features) from sklearn and perform exploratory analysis.

Base:
## Delta (Changes)


## Setup

- Python 3, scikit-learn, pandas, numpy, matplotlib, seaborn
- Iris dataset via `sklearn.datasets.load_iris()`

## Procedure

1. Load dataset and inspect structure (shape, dtypes, missing values)
2. Compute summary statistics (mean, std, min/max per feature and species)
3. Visualize: pairplot, histograms, box plots, sepal and petal scatter plots
4. Quantify overlap: per-feature range analysis across all species pairs

## Expected Results

If Iris species are linearly separable, we expect no feature-range overlap between at least one pair of features for each species pair, or a clear linear decision boundary in 2D feature space.

## Actual Results

- **Dataset**: 150 samples, 4 features, 3 balanced classes (50 each), no missing values.
- **Setosa**: Perfectly separable from versicolor and virginica on both petal features — zero range overlap.
- **Versicolor vs virginica**: Overlap in petal length [4.50, 5.10] (37 samples) and petal width [1.40, 1.80] (38 samples). Not linearly separable in the 2D petal space.
- **Sepal features**: Heavy overlap across all three species pairs.
- **Conclusion**: The hypothesis is **partially supported** — Iris species are not globally linearly separable, but setosa is. Versicolor and virginica require a non-linear boundary or more than 2 dimensions.


## Linked Evidence

- [[classifier-comparison-lr-vs-knn-on-iris-petal-features|Classifier comparison: LR vs KNN on Iris petal features]]

## Linked Hypothesis

- [[iris-species-are-linearly-separable|Iris species are linearly separable.]]
