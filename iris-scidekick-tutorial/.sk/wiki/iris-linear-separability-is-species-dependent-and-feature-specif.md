---
{title: Iris linear separability is species-dependent and feature-specific,type: insight,created: 2026-07-01T13:04:33.190Z,updated: 2026-07-01T13:04:33.191Z,tags: []}
---

# Insight: Iris linear separability is species-dependent and feature-specific

## Context

Two hypotheses were tested against the Iris dataset: (1) all three species are linearly separable, and (2) petal dimensions alone can discriminate them. EDA quantified overlap, and a formal classifier comparison (LR vs KNN) was cross-validated.

## Idea

Linear separability in the Iris dataset is **not binary** — it is species-dependent and feature-dependent:

1. **Setosa is trivially linearly separable** from versicolor and virginica using petal features alone. Zero range overlap in both petal length and petal width means a single hyperplane achieves perfect classification. This is true for any linear classifier.

2. **Versicolor and virginica are not linearly separable** in the 2D petal space. They overlap in petal length [4.50, 5.10] and petal width [1.40, 1.80], involving ~25% of their combined samples. Neither LR nor any linear model can achieve 100% accuracy on the full 3-class problem.

3. **Petal dimensions alone are sufficient for high accuracy, but not perfection.** Logistic regression on only petal length and width achieves 95.3% mean CV accuracy — above the 95% threshold — with all errors in the versicolor/virginica overlap zone. KNN (k=1) reaches 97.3%, but the difference is not statistically significant (*p* = .374).

The original hypothesis ("all Iris species are linearly separable") is therefore **rejected** as stated, but the refined claim ("petal dimensions discriminate with >95% accuracy") is **supported**.

## Implications

- Claims about Iris separability must specify *which species*, *which features*, and *what accuracy threshold*.
- The versicolor/virginica boundary is the hard problem — it likely requires non-linear methods (KNN, RBF SVM, trees) or additional features (sepal dimensions add ~2% accuracy) to approach 100%.
- The Iris dataset's reputation as "linearly separable" is an oversimplification. It is *largely* separable, but not perfectly — an important nuance for teaching and benchmarking.

## Related

- Hypothesis: [[iris-species-are-linearly-separable|Iris species are linearly separable.]] (rejected)
- Hypothesis: [[petal-dimensions-alone-discriminate-iris-species|Petal dimensions alone discriminate Iris species]] (proposed, partially supported)
- Experiment: [[iris-exploratory-data-analysis|Iris exploratory data analysis]]
- Evidence: [[classifier-comparison-lr-vs-knn-on-iris-petal-features|Classifier comparison: LR vs KNN on Iris petal features]]

## Action Items

- Test whether adding sepal features raises LR accuracy above 97% on the 3-class problem.
- Train a non-linear classifier (RBF SVM, random forest) to quantify the ceiling accuracy on petal features alone.
- Quantify the versicolor/virginica overlap with a proper margin analysis (distance to decision boundary).