# Task 2 – Classification using KNN and Support Vector Machines (SVM)

## Task Objective

The objective of this task is to perform **binary classification** using the provided `classified_data.txt` dataset. The task involves understanding feature behavior across classes, applying appropriate preprocessing, and building classification models using **K-Nearest Neighbors (KNN)** and **Support Vector Machines (SVM)**.

---

## Dataset Description

The dataset consists of:

* **10 numerical feature columns**
* **1 binary target column** (`TARGET CLASS`, values 0 and 1)

The features are already standardized, making the dataset suitable for distance-based and margin-based learning algorithms.

---

## Exploratory Data Analysis

To understand how features vary across the two target classes, **boxplots** were generated for each feature with respect to `TARGET CLASS`.

### Observations:

* Several features show noticeable shifts in median values between the two classes.
* Most features exhibit significant overlap, indicating that no single feature can perfectly separate the classes.
* Outliers are present in both classes across multiple features.
* The degree of overlap suggests a **non-linear classification problem**.

This analysis indicates that classification requires the **combined influence of multiple features**, rather than reliance on any single feature.

---

## Model 1: K-Nearest Neighbors (KNN)

### Motivation

KNN is a **distance-based algorithm**, so proper feature scaling is essential. Since all features are on comparable scales, KNN is an appropriate baseline classifier.

### Steps Performed

1. Separated features and target variable (`TARGET CLASS`)
2. Standardized feature values using `StandardScaler` (excluding the target)
3. Split the data into training and testing sets:

   * Test size = 30%
   * Fixed random seed for reproducibility
4. Trained a KNN classifier with an initial value of `n_neighbors = 1`
5. Evaluated performance using accuracy and classification report

### Hyperparameter Tuning

* Trained KNN models for values of `n_neighbors` ranging from **1 to 60**
* Recorded test accuracy for each value
* Plotted **K vs Accuracy** to analyze performance trends
* Selected the optimal K based on the highest test accuracy

### Key Insights (KNN)

* Very small values of K result in high variance and unstable decision boundaries.
* Very large values of K lead to oversmoothing and underfitting.
* An intermediate value of K provides the best bias–variance trade-off.

---

## Model 2: Support Vector Machine (SVM)

### Motivation

SVM is well-suited for this dataset because:

* The data is already scaled
* The classes are not linearly separable
* SVM performs well in high-dimensional feature spaces

A non-linear kernel (RBF) was chosen to capture complex decision boundaries.

### Key Observations (SVM)

* No single feature dominates class separation.
* Classification depends on the interaction between multiple features.
* Non-linear decision boundaries are necessary for effective classification.

---

## Key Findings

* The dataset represents a realistic classification problem with overlapping class distributions.
* No feature alone is sufficient for accurate classification.
* Both KNN and SVM benefit from proper preprocessing and scaling.
* KNN performance is highly sensitive to the choice of K.
* SVM is well-suited for capturing non-linear patterns present in the data.

---

## Files in This Branch

* `KrishK_GDG_Task2.ipynb` – Complete implementation of EDA, KNN, SVM, and evaluation
* `README.md` – Task documentation and summary

---

## Conclusion

Task 2 demonstrates the complete workflow of a classification problem, from exploratory analysis and preprocessing to model training and evaluation. Boxplot analysis helped reveal the non-linear nature of the dataset, guiding the choice of appropriate models. Through systematic experimentation with KNN and SVM, the task highlights the importance of preprocessing, hyperparameter tuning, and model selection in classification tasks.
