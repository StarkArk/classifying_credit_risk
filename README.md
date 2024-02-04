# classifying_credit_risk

## Overview of the Analysis

For Banks and Lenders, determining whether a potential borrower will repay when given a loan is key. Defaults rates have tended to be [around 3% in recent years](https://www.milliman.com/en/insight/milliman-mortgage-default-index-2023-q3). 
Lender's are always striving to improve and reduce the number of high-risk loans they extend. Generally, reducing the default rate can be beneficial to both a bank's profitability and a
borrower's actual interest rates.

In this project I look at some labeled loan data that includes high risk and healthy loans. The objective is to train a model to effectively detect 'bad' loans from
features that a bank might be presented with prior to extending a new loan.  

## Data and Analysis

The lending data includes information on the loan size, interest rate, income, debt to income, number of borrower accounts, number of derogatory marks(such as missed payments, 
bankruptcies,..., etc.), total debt for the borrower, and the labeled data 'loan status'(high risk - 1, healthy - 0).

[Lending Data](https://github.com/StarkArk/classifying_credit_risk/blob/main/Credit_Risk/lending_data.csv)

#### The data:
	- 77,536 loans&emsp; ensp; nbsp;
	- 2,500 of which are labeled high-risk "1"
	- 75,536 labeled healthy "0"
	
* 7 Features/Columns:
	* loan_size &emsp; &ensp; &nbsp; &ensp; &nbsp; -Loan Amount
	* interest_rate &emsp; &ensp; &nbsp; &ensp; &nbsp; -Interest Rate
	* borrower_income &emsp; &nbsp; -Borrower's Annual Gross Income
	* debt_to_income &ensp; &ensp; -The Ratio of Borrower's Monthly Debt to their Income
	* num_of_accounts &emsp; &nbsp; -Total number of borrower accounts
	* derogatory_marks &emsp; -Number of missed payments, bankruptcies,..., etc. 
	* total_debt  <center>-Total Amount of Debt carried by the borrower</center>

&emsp; &ensp; &nbsp; &ensp;

Logistic Regression was used to train the prediction model. We tested two resampling techniques, one that took the labeled data in the proportion that it had in the sample and another
that oversampled the 'high risk' loan data.

Analysis: [Notebook](https://github.com/StarkArk/classifying_credit_risk/blob/main/Credit_Risk/credit_risk_classification.ipynb)

## Results

### Logistic Regression Model scores comparing Sampled and Oversampled techniques.

#### **---Balanced Accuracy---**

  Sampled: 95.2% <br>
  OverSampled: 99.37%

#### **---Confusion Martrices---**

KEY:
[['True Positive', 'False Positive'] <br>
 ['False Negative', 'True Positive']]

  ---Sampled---

[[18663,   102] <br>
 [   56,   563]]

  ---OverSampled---

[[18649,   116] <br>
 [    4,   615]]

#### **---Classification Tables---**

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


**Healthy Loans:** The model predictions, sampled and oversampled, were accurate with relatively few false positives(Precision 1.00) and false negatives(Recall .99). 

**Ordinary Sampled Method:** The predictions for high risk loans were less accurate with relatively more false positives(Precision .85) and false negatives(Recall .91). Ideally, we would 
like to reduce the false negatives for high risk loans to find more of the high-risk loans that lenders would prefer to avoid.

**OverSampled Method:** Oversampling significantly reduced the # of false negatives, from 56 down to 4. Successfully detecting more high-risk loans compared to the less balanced original 
training sample (615 vs 563). False positives, loans eroneously labeled 'high-risk', did increase. This is acceptable given that a bank should be more focused on avoiding/reducing bad 
loans rather than picking up a marginal number of 'healthy' loans.

**Overall:** The OverSampled Method was superior, with a higher balanced accuracy (99.4% vs 95.2%) and fewer False Negatives (4 vs 56), correctly labelling more of the high risk loans 
(615 vs 563).

## Refererences

1. Milliman's Mortgage Default Index: [2023-Q3](https://www.milliman.com/en/insight/milliman-mortgage-default-index-2023-q3).
2. Benefits of Machine Learning on Mortgage Lending. [Link](https://plat.ai/blog/machine-learning-mortgage-lending/)
3. Data for this dataset was provided by edX Boot Camps LLC.