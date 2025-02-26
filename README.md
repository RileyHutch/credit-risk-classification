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
The purpose of this analysis was to use machine learning to predict if loans were considered **"healthy" (0) or "high-risk" (1)** depending on seven different financial factors provided. At the end of it we measured how accurately our learning model was  classifying these loans. 

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

### **Basic information about our prediction variable `loan_status`**

In this project we are looking to predict `loan_status`. I used the len function and .value_counts to see that healthy loans accounted for 97% of the data while high-risk loans accounted for only 3%. This is a significant difference and may impact our ability to accurately predict high-risk loans due to not having many examples to learn from.

### **Machine Learning Process**
1. **Data Preprocessing**
    - Seperated the df to create the label and the features
    - Splitted the dataset into training (80%) and testing (20%) sets
    
2. **Model Selection & Training**
    - **Logistic Regression (`liblinear` solver)**: Chosen due to its efficiency in binary classification problems
    - **Applied Class Balancing Techniques**: Since the dataset was imbalanced (97% healthy loans vs. 3% high-risk loans), I used `class_weight='balanced'` to improve recall on high-risk loans.

3. **Model Evaluation**
    - Generated a **confusion matrix** and a **classification report**
    - Evaluated model performance using **accuracy, precision, recall, and F1-score**

## Results

### **Logistic Regression Model Performance**                         
- **Accuracy**: **100%**
- **Precision**:
  - `0` (Healthy Loans): **1.00**
  - `1` (High-Risk Loans): **0.87**
- **Recall**:
  - `0` (Healthy Loans): **1.00**
  - `1` (High-Risk Loans): **1.00**
- **F1-score**:
  - `0` (Healthy Loans): **1.00**
  - `1` (High-Risk Loans): **0.93**

## Summary and Recomnedation

The model demonstrates exceptional performance in credit risk classification, with a confusion matrix showing 18,668 true negatives, 91 false positives, 2 false negatives, and 623 true positives. The classification report confirms perfect scores for non-risk cases and strong performance for risk cases, with a precision of 0.87 and a recall of 1.00 for the risk class, ensuring nearly all risky cases are detected. This high recall is particularly critical in credit risk scenarios where missing a high-risk applicant can be costly. Although there is a slight drop in precision leading to a few false positives, this trade-off is acceptable given the priority to avoid missed risks. Therefore, the model is recommended for use by the company, with the option to further adjust the decision threshold if minimizing false positives becomes a priority.