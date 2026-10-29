# ML-Project-Kickoff
# Wine Classification: Machine Learning Mini-Project

## Project Overview

This project explores the use of machine learning algorithms to classify wine samples into three different classes based on their chemical properties.

Using the Wine Recognition dataset available in `scikit-learn`, several classification models were trained and evaluated to compare their performance and identify which approaches produced the most reliable results.

The main goal was to understand how data preprocessing, feature scaling, feature selection, and ensemble learning affect classification performance.

## Objectives

- Explore and prepare a real-world dataset for classification.
- Build and compare different machine learning models.
- Evaluate model performance using accuracy and cross-validation.
- Investigate the impact of feature scaling and feature selection.
- Identify the most influential features in the Random Forest model.
- Discuss the limitations and potential applications of the results.

## Dataset

The project uses the **Wine Recognition dataset** included in `scikit-learn`.

- **Number of samples:** 178
- **Number of features:** 13
- **Number of target classes:** 3
- **Missing values:** None found during the initial data checks.

The features represent chemical measurements of wine samples, including alcohol, malic acid, ash, flavanoids, color intensity, hue, proline, and other chemical properties.

The target variable represents the wine class.

## Methodology

### 1. Data Exploration and Preparation

The dataset was loaded using `sklearn.datasets.load_wine`. Initial exploration included checking the dataset structure, data types, target distribution, and missing values.

The data was split into training and testing sets using an **80/20 split**, stratification, and `random_state=42`.

### 2. Feature Engineering and Selection

Feature scaling was applied to improve the performance of K-Nearest Neighbors (KNN), an algorithm that relies on distances between samples.

The project compared:

- KNN using the original features.
- KNN after feature scaling.
- KNN after feature scaling and selecting the 10 best features using `SelectKBest` with an ANOVA F-test.

### 3. Model Building

The following model configurations were evaluated:

- K-Nearest Neighbors (KNN)
- Scaled KNN
- Scaled KNN with feature selection
- Bagging Classifier
- Pasting Classifier
- Random Forest Classifier

### 4. Model Evaluation

Model performance was evaluated using test-set accuracy. Five-fold stratified cross-validation was also used to compare mean accuracy and variability across folds.

Additional classification metrics, including precision, recall, F1-score, and the confusion matrix, were examined for KNN.

**Note:** Grid search and systematic hyperparameter tuning were not performed in this version of the project. These are proposed as future improvements.

## Results

### Test Set Performance

| Model | Test Accuracy |
|---|---:|
| Bagging Classifier | 100.00% |
| Random Forest Classifier | 100.00% |
| Scaled KNN | 97.22% |
| Scaled KNN + Feature Selection | 97.22% |
| Pasting Classifier | 97.22% |
| Original KNN | 80.56% |

Bagging and Random Forest correctly classified all 36 samples in the test set. Scaled KNN and scaled KNN with feature selection each achieved 97.22% accuracy, while the original KNN model achieved 80.56%.

### Five-Fold Cross-Validation

| Model | Mean Accuracy | Standard Deviation |
|---|---:|---:|
| Random Forest | 97.75% | 2.13% |
| Scaled KNN | 97.17% | 1.81% |
| Bagging Classifier | 96.62% | 3.31% |
| Pasting Classifier | 94.94% | 4.18% |
| Original KNN | 68.02% | 4.27% |

Random Forest achieved the highest mean cross-validation accuracy at 97.75%, followed closely by scaled KNN at 97.17%.

The results also show that scaling substantially improved KNN performance.

### Feature Importance

The Random Forest model identified the following features as the most influential:

1. Color intensity — 18.76%
2. Flavanoids — 15.96%
3. Proline — 14.68%
4. Alcohol — 11.79%
5. Hue — 10.15%
6. OD280/OD315 of diluted wines — 9.63%

These importance scores describe how the fitted Random Forest model used the features. They do not establish causal relationships.

## Key Findings

- Feature scaling substantially improved KNN performance.
- Feature selection reduced the number of input features from 13 to 10 while maintaining the same test accuracy as scaled KNN.
- Bagging and Random Forest achieved perfect accuracy on this particular test split.
- Random Forest obtained the highest mean accuracy in five-fold cross-validation.
- Cross-validation provides additional context beyond a single train-test split.

## Limitations

The dataset contains only 178 samples, and the test set contains 36 samples. Consequently, a perfect test score does not guarantee that a model will perform equally well on new, independent data.

The dataset also represents a limited number of wine classes and should not be assumed to represent every wine type or production context.

The project is an educational classification exercise, not a validated commercial wine-quality assessment system.

## Future Improvements

Possible next steps include:

- Using `GridSearchCV` to optimize model hyperparameters.
- Applying feature selection within a cross-validation pipeline to reduce evaluation bias.
- Evaluating the final model on a larger, independent dataset.
- Comparing per-class precision, recall, F1-scores, and confusion matrices across models.
- Documenting the full reproducible workflow and final model configuration.

## Technologies Used

- Python
- pandas
- NumPy
- scikit-learn
- Matplotlib / Seaborn, if used for visualizations
- Jupyter Notebook

## How to Run the Project

1. Clone or download this repository.
2. Install the required Python libraries.
3. Open the project notebook in Jupyter Notebook or JupyterLab.
4. Run the notebook cells in order.

Install the core dependencies with:

```bash
pip install numpy pandas scikit-learn matplotlib seaborn jupyter
```

Some libraries in this command may be unnecessary if they were not used in the final notebook.

## Conclusion

This project demonstrates how machine learning can classify wine samples using chemical measurements. The experiments highlight the importance of preprocessing and model evaluation. Although ensemble models achieved excellent test results, five-fold cross-validation and further testing on independent data are necessary to better assess generalization.

---

**Project:** Wine Classification  
**Context:** Ironhack Machine Learning Mini-Project  
**Dataset:** Wine Recognition dataset from scikit-learn

