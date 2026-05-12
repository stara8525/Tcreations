# Data

This project uses the Breast Cancer Wisconsin dataset available through `sklearn.datasets.load_breast_cancer`.

The dataset is not stored directly in this repository because it is loaded programmatically from scikit-learn.

Each row represents a tumor sample, and the features describe physical measurements of cell nuclei. The target variable indicates diagnosis:

| Target | Diagnosis |
|---|---|
| 0 | Malignant |
| 1 | Benign |

In the analysis notebook, the target was transformed so that:

| Transformed Target | Diagnosis |
|---|---|
| 1 | Malignant |
| 0 | Benign |

This was done to make ROC AUC interpretation more focused on identifying malignant tumors.