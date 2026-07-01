# Methods

## Dataset

The Iris flower dataset (Fisher, 1936; Anderson, 1935) was obtained via `sklearn.datasets.load_iris` (Pedregosa et al., 2011). The dataset comprises 150 samples from three Iris species — *Iris setosa*, *Iris versicolor*, and *Iris virginica* — with 50 samples per class. Four continuous morphological features were recorded for each sample: sepal length, sepal width, petal length, and petal width (all in cm). No samples contained missing values.

## Feature Selection

Prior exploratory data analysis identified petal length and petal width as the dominant discriminative features: *I. setosa* exhibits zero range overlap with the other two species in both petal dimensions, while sepal features show heavy overlap across all three classes. Consequently, the primary analysis used only the two petal features. A secondary analysis included all four features for ceiling estimation. Features were standardized to zero mean and unit variance within each cross-validation fold via `sklearn.preprocessing.StandardScaler` to prevent data leakage.

## Classification Models

Two supervised classifiers were compared:

**Logistic regression.** Multinomial logistic regression (Nelder & Wedderburn, 1972) was implemented via `sklearn.linear_model.LogisticRegression` with default regularization strength (*C* = 1.0), the LBFGS solver, and a maximum of 1,000 iterations. Hyperparameter tuning via grid search over *C* ∈ {0.01, 0.1, 1, 10, 100} with three-fold inner cross-validation confirmed that the default (*C* = 1.0) was optimal.

**K-nearest neighbors.** A *k*-nearest neighbors classifier (Cover & Hart, 1967) was implemented via `sklearn.neighbors.KNeighborsClassifier` with Euclidean distance metric. The number of neighbors *k* was selected via grid search over {1, 3, 5, …, 29} with stratified five-fold cross-validation. The optimal value was *k* = 1. To assess whether this represented a meaningful advantage over *k* = 3 (a more conventional choice robust to noise), secondary analyses were conducted with both values.

## Evaluation Procedure

**Primary cross-validation.** Both classifiers were evaluated using stratified five-fold cross-validation (`sklearn.model_selection.StratifiedKFold`) with identical fold assignments across models, ensuring paired comparisons. The random seed was fixed at 42 for reproducibility. Performance metrics included accuracy, per-class precision, recall, and F₁-score.

**Repeated cross-validation.** To assess the stability of the primary result and obtain reliable effect-size estimates, a repeated cross-validation design was employed: 100 independent repetitions of stratified five-fold cross-validation with distinct random seeds, yielding 500 paired fold-level accuracy estimates per classifier. This design provides sufficient statistical power (1 − β > 0.99 at α = .05) to detect effect sizes as small as Cohen's *d* = 0.06.

## Statistical Analysis

All analyses were conducted in Python 3.9 using `scikit-learn` 1.5, `scipy` 1.13, `pandas` 2.2, and `numpy` 1.26.

**Classifier comparison.** The primary comparison between logistic regression and *k*-nearest neighbors used the paired fold-level accuracy differences from the repeated cross-validation design (*N* = 500 folds). A paired-samples *t*-test evaluated the null hypothesis of equal mean accuracy. Effect size was quantified with Cohen's *d* (mean difference divided by the pooled standard deviation of the paired differences). A 95% confidence interval was computed for the mean difference.

**Supplementary tests.** Two supplementary tests were conducted on the original five-fold split to corroborate the primary result: (a) a Wilcoxon signed-rank test as a non-parametric alternative given the small number of folds, and (b) McNemar's test on the paired per-sample predictions (*N* = 150) to compare classifier agreements on identical test samples.

**Assumption checks.** Normality of the paired accuracy differences was assessed with the Shapiro-Wilk test. For the repeated cross-validation design, the Central Limit Theorem ensures approximate normality of the sampling distribution of mean differences given *N* = 500 folds, so no additional distributional assumptions were invoked.

**Multiple comparisons.** The primary *t*-test on repeated CV differences was the sole confirmatory test. The supplementary Wilcoxon and McNemar tests on the five-fold split are reported as descriptive checks only. The family-wise error rate for the original three-test suite (t, Wilcoxon, McNemar) was not corrected, as these tests were superseded by the repeated CV analysis.

**Reporting standards.** All statistical results are reported in APA 7th edition format with exact *p*-values (rounded to three decimal places unless *p* < .001), degrees of freedom, test statistics, effect sizes, and 95% confidence intervals. Mean values are reported with standard deviations as *M* ± *SD*.

## Software Availability

All code, data, and analysis scripts are available in the project repository. The Iris dataset is in the public domain and distributed with scikit-learn under the BSD 3-Clause license.

---

## References

Anderson, E. (1935). The irises of the Gaspé Peninsula. *Bulletin of the American Iris Society*, *59*, 2–5.

Cover, T., & Hart, P. (1967). Nearest neighbor pattern classification. *IEEE Transactions on Information Theory*, *13*(1), 21–27. https://doi.org/10.1109/TIT.1967.1053964

Fisher, R. A. (1936). The use of multiple measurements in taxonomic problems. *Annals of Eugenics*, *7*(2), 179–188. https://doi.org/10.1111/j.1469-1809.1936.tb02137.x

Nelder, J. A., & Wedderburn, R. W. M. (1972). Generalized linear models. *Journal of the Royal Statistical Society: Series A*, *135*(3), 370–384. https://doi.org/10.2307/2344614

Pedregosa, F., Varoquaux, G., Gramfort, A., Michel, V., Thirion, B., Grisel, O., … Duchesnay, É. (2011). Scikit-learn: Machine learning in Python. *Journal of Machine Learning Research*, *12*, 2825–2830.
