# Breast Cancer Diagnosis: Feature-Based Classification Analysis

## Project Overview

This project explores whether physical measurements of tumor cell nuclei can help distinguish between benign and malignant breast tumors.

Using the breast cancer dataset from `sklearn`, I analyzed several features related to tumor size, texture, and shape, then compared how well different feature combinations predicted malignancy using logistic regression and ROC AUC.

## Research Question

Can physical characteristics of tumor cell nuclei be used to distinguish between benign and malignant tumors?

More specifically:

- How predictive are individual features such as mean radius, mean texture, and mean concavity?
- Does combining multiple physical features improve classification performance?

## Dataset

The dataset used in this project is the Breast Cancer Wisconsin dataset available through `sklearn.datasets`.

Each row represents a tumor sample. The dataset includes physical measurements of cell nuclei, such as:

- Mean radius
- Mean texture
- Mean concavity
- Mean smoothness
- Mean area

The target variable indicates diagnosis:

| Target | Diagnosis |
|---|---|
| 0 | Malignant |
| 1 | Benign |

For model evaluation, I transformed the target so that:

| Transformed Target | Diagnosis |
|---|---|
| 1 | Malignant |
| 0 | Benign |

This made the AUC interpretation more focused on identifying malignant tumors.

## Methods

The analysis followed these steps:

1. Loaded the dataset into a pandas DataFrame
2. Checked the target labels and class balance
3. Explored individual features using summary statistics and visualizations
4. Compared feature overlap between benign and malignant tumors
5. Built logistic regression models using different feature sets
6. Evaluated model performance using ROC AUC

## Features Analyzed

The main features analyzed were:

| Feature | Interpretation |
|---|---|
| Mean radius | Average size of the tumor cell nuclei |
| Mean texture | Variation in grayscale intensity |
| Mean concavity | Degree of concave regions in the cell nuclei boundary |

These features were chosen because they represent different physical characteristics:

- Size
- Texture
- Shape irregularity

## Results

### AUC Model Comparison

| Feature Set | AUC |
|---|---:|
| Mean Texture | 0.762 |
| Mean Concavity | 0.961 |
| Mean Radius | 0.970 |
| Mean Radius + Mean Texture | 0.973 |
| Mean Radius + Mean Texture + Mean Concavity | 0.979 |

## Interpretation

Mean radius was the strongest single-feature predictor, achieving an AUC of approximately 0.970. This suggests that tumor size provides strong separation between malignant and benign tumors.

Mean concavity also performed strongly, with an AUC of approximately 0.961, suggesting that shape irregularity is also an important indicator of malignancy.

Mean texture was moderately predictive, with an AUC of approximately 0.762, but it was weaker than both radius and concavity.

The best-performing model used mean radius, mean texture, and mean concavity together, achieving an AUC of approximately 0.979. This suggests that combining size, texture, and shape-based features improves classification performance, although the improvement over mean radius alone was relatively small.

## Key Takeaways

- Physical measurements of tumor cell nuclei can provide meaningful information about malignancy.
- Mean radius and mean concavity were the strongest individual predictors.
- Mean texture added some information but was less predictive on its own.
- Combining multiple features produced the highest AUC.
- The improvement from adding more features was modest because mean radius alone was already highly predictive.

## Limitations

This project is an introductory exploratory analysis and has several limitations:

- Only a small subset of features was analyzed.
- Logistic regression was the only classification model used.
- The analysis focused mainly on ROC AUC and did not deeply examine other metrics such as recall, precision, or false negatives.
- The dataset is clean and built-in, so it does not fully represent the messiness of real-world clinical data.

## Future Work

Future extensions could include:

- Testing additional features from the dataset
- Comparing more models, such as decision trees, random forests, or support vector machines
- Evaluating recall for malignant tumors specifically
- Creating ROC curves for visual model comparison
- Performing cross-validation for more robust evaluation

## Tools Used

- Python
- pandas
- matplotlib
- scikit-learn
- VS Code
- Jupyter Notebook

## Project Files

```text
cancer-diagnosis-project/
├── notebooks/
│   └── 01_exploration.ipynb
├── data/
└── README.md