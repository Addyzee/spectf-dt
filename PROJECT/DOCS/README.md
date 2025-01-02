# SPECTF Heart Dataset Analysis Documentation

## Overview
This project implements and analyzes Decision Tree Classifiers on the SPECTF heart dataset. The main goal is to evaluate different decision tree configurations and their performance in diagnosing cardiac abnormalities based on Single Proton Emission Computed Tomography (SPECT) images.

## Dataset
- **Source**: SPECTF Heart Dataset
- **Features**: Multiple SPECT image measurements
- **Target Variable**: OVERALL_DIAGNOSIS (Binary classification: Normal vs Abnormal)
- **Size**: Split into training and test sets

## Implementation Components

### 1. Custom Cross-Validation
- Implements 100 trials of 10-fold cross-validation implemented without scikit learn
- Evaluates performance for different tree depths:
  - Decision Stump (depth=1)
  - 3-level tree (depth=3)
  - Unlimited depth tree
- Calculates mean accuracy and standard deviation across trials

### 2. Learning Curve Analysis
![Learning curve for the different classifiers](/spectf-lc.png)
- Evaluates model performance across different training set sizes (10% to 100%)
- Compares multiple tree depths
- Visualizes performance with standard deviation bands
- Helps identify potential overfitting/underfitting issues

### 3. Model Optimization
- Grid search for optimal hyperparameters
- Parameters tuned:
  - max_depth: [1, 3, 5, 7, 10, 13]
  - min_samples_leaf: [1, 5, 10, 20, 29]

### 4. Performance Evaluation
- Classification metrics:
  - Accuracy scores (train and test)
  - Classification report
  - Confusion matrix
       ![Confusion matrix for the best classifier](/spectf-cm.png)
  - Visual tree structure analysis
    ![Decision tree](/spectf-dt2.png)
  - ROC curve analysis
  ![ROC curve](/spectf-roc.png)


## Key Results
- Decision stump (depth=1) showed surprisingly good performance
- Higher depth trees showed signs of overfitting
- Model performance stabilized with increasing training data
- Best performing model achieved reasonable accuracy on test set

## Dependencies
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

## Usage
1. Load the SPECTF dataset
2. Run custom cross-validation evaluation
3. Generate learning curves
4. Perform grid search optimization
5. Evaluate final model performance

## Future Improvements
- Feature importance analysis
- Additional hyperparameter tuning
- More advanced tree pruning techniques
- Ensemble methods comparison