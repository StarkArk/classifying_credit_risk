# classifying_credit_risk

## Overview of the Analysis

For Banks and Lenders, determining whether a potential borrower will repay when given a loan is key. Defaults rates have tended to be [around 3% in recent years](https://www.milliman.com/en/insight/milliman-mortgage-default-index-2023-q3). 
Lender's are always striving to improve and reduce the number of high-risk loans they extend. Generally, reducing the default rate can be beneficial to both a bank's profitability and
borrower actual interest rates.

In this project I look at some labelled loan data that includes high risk and healthy loans. The objective is to train a model to effectively detect 'bad' loans from
features that a bank might be presented with prior to extending a new loan.  

## Data and Analysis

The lending data includes information on the loan size, interest rate, income, debt to income, number of borrower accounts, number of derogatory marks(such as missed payments, 
bankruptcies,..., etc.), total debt for the borrower, and the labelled data 'loan status'(high risk - 1, healthy - 0).

[Lending Data](https://github.com/StarkArk/classifying_credit_risk/blob/main/Credit_Risk/lending_data.csv)

In the data:
	75,036 are healthy loans
	2,500 are labelled high-risk 

Logistic Regression was used to train the prediction model. We tested two resampling techniques, one that took the labelled data in the proportion that it had in the sample and another
that oversampled the 'high risk' loan data.

Analysis: [Notebook]()

* Explain the purpose of the analysis.
* Explain what financial information the data was on, and what you needed to predict.
* Provide basic information about the variables you were trying to predict (e.g., `value_counts`).
* Describe the stages of the machine learning process you went through as part of this analysis.
* Briefly touch on any methods you used (e.g., `LogisticRegression`, or any resampling method).

## Results

### Logistic Regression Model scores comparing Sampled and Oversampled techniques.

---Balanced Accuracy---

  Sampled: 95.2%
  OverSampled: 99.37%

---Confusion Martrices---

KEY:
[['True Positive', 'False Positive'
 ['False Negative', 'True Positive']]

  ---Sampled---

[[18663   102]
 [   56   563]]

  ---OverSampled---

[[18649   116]
 [    4   615]]

---Classification Tables---

  ---Sampled---

                 precision    recall  f1-score   support

  healthy loans       1.00      0.99      1.00     18765
high-risk loans       0.85      0.91      0.88       619

       accuracy                           0.99     19384
      macro avg       0.92      0.95      0.94     19384
   weighted avg       0.99      0.99      0.99     19384


  ---OverSampled---

                 precision    recall  f1-score   support

  healthy loans       1.00      0.99      1.00     18765
high-risk loans       0.84      0.99      0.91       619

       accuracy                           0.99     19384
      macro avg       0.92      0.99      0.95     19384
   weighted avg       0.99      0.99      0.99     19384

## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:
The logistic regression model predictions for healthy loans were accurate with relatively few false positives(Precision 1.00) and false negatives(Recall .99). 

**Ordinary Sampled Method:** The predictions for high risk loans are less accurate with relatively more false positives(Precision .85) and false negatives(Recall .91). Ideally, we would 
like to reduce the false negative for high risk loans so that we find more of the high-risk loans that Banks would be best off avoiding

**OverSampled Method:** Oversampling significantly reduced the # of false negatives, from 56 down to 4. Successfully detecting more high-risk loans compared to the less balanced original 
training sample (615 vs 563). False positives, loans eroneously labeled 'high-risk', did increase. This is acceptable given that a bank should be more focused on avoiding/reducing bad 
loans rather than picking up a marginal number of 'healthy' loans.

