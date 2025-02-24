# Module 12 Report Template

## Overview of the Analysis

In this section, describe the analysis you completed for the machine learning models used in this Challenge. This might include:

* Explain the purpose of the analysis.
* Explain what financial information the data was on, and what you needed to predict.
* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).
* Describe the stages of the machine learning process you went through as part of this analysis.
* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any other algorithms).

## Results

Using bulleted lists, describe the accuracy scores and the precision and recall scores of all machine learning models.

* Machine Learning Model 1:
    * Description of Model 1 Accuracy, Precision, and Recall scores.

## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:

* Which one seems to perform best? How do you know it performs best?
* Does performance depend on the problem we are trying to solve? (For example, is it more important to predict the `1`'s, or predict the `0`'s? )

If you do not recommend any of the models, please justify your reasoning.





















# Module 12 Report

## Overview of the Analysis

### **Purpose of the Analysis**
The goal of this analysis was to develop and evaluate machine learning models to predict the likelihood of a loan being classified as either **"healthy" (0) or "high-risk" (1)**. Using historical financial data, we aimed to assess how accurately a model can classify loans and help in making better risk-based lending decisions.

### **Dataset and Prediction Objective**
The dataset contains **financial information** on borrowers, including:
- Loan size
- Interest rate
- Borrower income
- Debt-to-income ratio
- Number of accounts
- Derogatory marks
- Total debt
- Loan status (target variable: 0 for "healthy loan" and 1 for "high-risk loan")

The objective was to predict whether a loan is **high-risk (`1`) or healthy (`0`)** based on these features.

### **Machine Learning Process**
1. **Data Preprocessing**
    - Checked for missing values (✅ No missing values found)
    - Splitted the dataset into training (80%) and testing (20%) sets
    - Scaled features using `StandardScaler` to improve model performance
    
2. **Model Selection & Training**
    - **Logistic Regression (`liblinear` solver)**: Chosen due to its efficiency in binary classification problems
    - **Applied Class Balancing Techniques**: Since the dataset was imbalanced (96.8% healthy loans vs. 3.2% high-risk loans), we used `class_weight='balanced'` to improve recall on high-risk loans.

3. **Model Evaluation**
    - Generated a **confusion matrix**
    - Evaluated model performance using **accuracy, precision, recall, and F1-score**

## Results

### **Logistic Regression Model Performance**                          This section isn't correct
- **Accuracy**: **88%**
- **Precision**:
  - `0` (Healthy Loans): **0.98**
  - `1` (High-Risk Loans): **0.50**
- **Recall**:
  - `0` (Healthy Loans): **0.99**
  - `1` (High-Risk Loans): **0.30**
- **F1-score**:
  - `0` (Healthy Loans): **0.98**
  - `1` (High-Risk Loans): **0.37**

## Summary

### **Best Model Selection**
- The **Logistic Regression model** performed well with an **overall accuracy of 88%**.
- However, the recall for class `1` (high-risk loans) was low (**30%**), meaning the model **misses a significant number of high-risk loans**.

### **Performance Considerations**
- If the goal is to **minimize risk and correctly detect high-risk loans**, we should **increase recall for `1`**.
- If we focus on **accurate loan approvals**, the current model performs well for `0` (healthy loans) but risks misclassifying too many high-risk loans.

### **Recommendation**
- To **improve high-risk loan detection**, we recommend:
  - **Using SMOTE** (Synthetic Minority Oversampling) to balance the dataset
  - **Trying a different algorithm** (e.g., Random Forest or XGBoost) to improve recall
  - **Adjusting classification thresholds** to increase sensitivity to high-risk loans

If catching **high-risk loans** is the priority, further improvements are needed before deploying this model. 🚀

