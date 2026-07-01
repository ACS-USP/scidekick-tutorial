---
{title: "Classifier comparison: LR vs KNN on Iris petal features",type: evidence,created: 2026-07-01T12:58:58.102Z,updated: 2026-07-01T12:58:58.104Z,tags: [],source_hypothesis: "petal-dimensions-alone-discriminate-iris-species",source_experiment: "iris-exploratory-data-analysis",strength: moderate}
---

# Evidence: Classifier comparison: LR vs KNN on Iris petal features

## Source

- Hypothesis: [[petal-dimensions-alone-discriminate-iris-species|Petal dimensions alone discriminate Iris species]]
- Experiment: [[iris-exploratory-data-analysis|Iris exploratory data analysis]]

## Finding

Logistic regression and *k*-nearest neighbors (*k* = 1) were compared on the Iris dataset (*N* = 150) using petal length and petal width as predictors, with species as the three-level target. Both classifiers were evaluated via stratified five-fold cross-validation with identical fold assignments.

- **Logistic regression**: mean CV accuracy = 0.953 (*SD* = 0.051)
- **KNN (k = 1)**: mean CV accuracy = 0.973 (*SD* = 0.015)

A paired-samples *t*-test found no statistically significant difference, *t*(4) = −1.00, *p* = .374, Cohen's *d* = 0.45. A Wilcoxon signed-rank test (*W* = 1.0, *p* = .276) and McNemar's test on per-sample predictions (5 discordant pairs, *p* = .375) confirmed the null result.

Setosa was classified perfectly by both models (precision = recall = 1.000). All errors (LR: 7; KNN: 4) occurred in the versicolor–virginica overlap zone.

## Strength Assessment

Strength: moderate

## Interpretation

Both classifiers support the hypothesis that petal dimensions alone discriminate Iris species with high accuracy (>95%). KNN achieved numerically higher accuracy than LR, but the difference is not statistically reliable. The small number of CV folds (*k* = 5) limits power — approximately 40 folds would be required to detect a difference of this magnitude (Cohen's *d* = 0.45) at 80% power and α = .05.

## Limitations

- Five-fold CV provides limited statistical power for classifier comparison.
- KNN with *k* = 1 is effectively a lookup table and may not generalize to noisy data.
- Results are specific to the Iris dataset; the small, clean nature of the dataset favors both models.
- The difference, if real, is small (Cohen's *d* = 0.45) and may not be practically meaningful.