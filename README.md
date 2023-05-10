# Credit Risk Classification

## Overview of the Analysis

This analysis, conducted using Python, looks at a total of 77,536 loans and data related to each loan to construct a computational model that may be used to predict the likelihood of whether a loan is healthy or has a high risk of defaulting.  A total of seven factors were considered when constructing this prediction model: (1) loan amount, (2) interest rate, (3) borrower’s income, (4) borrower’s debt to income ratio, (5) number of accounts the borrower had at the time of the loan, (6) the number of derogatory marks on the borrower’s loan report, (7) borrower’s total debt.

A linear logistic regression model from the SKLearn library was instantiated, the original data was split (75% went to training, 25% went to testing) and the model was trained with the training set.  The testing set was then used to assess the accuracy of the model at predicting healthy versus high-risk loans.  A second analysis was done using the imbalanced-learn library to assess the effects of the imbalance within the original dataset (2,500 high-risk loans versus 75,036 healthy loans).


## Results

* **Machine Learning Model 1 (original data)**:
  * overall accuracy score = 99%

* Performance of model predicting healthy loans (‘0’)
	* precision = 100%
	* recall = 99%
	* f1-score = 100%
	* sample size = 18,765

* Performance of model predicting high-risk loans (‘1’)
	* precision = 85%
	* recall = 91%
	* f1-score = 88%
	* sample size = 619

* **Machine Learning Model 2 (RandomOverSampler):**
  * overall accuracy score = 99%
* Performance of model predicting healthy loans (‘0’)
	* precision = 100%
	* recall = 99%
	* f1-score = 100%
	* sample size = 18,905

* Performance of model predicting high-risk loans (‘1’)
	* precision = 99%
	* recall = 100%
	* f1-score = 99%
	* sample size = 18,613

## Summary

The logistic regression model using the original data had an overall accuracy score of 85% at prediciting whether a loan would eventually be considered healthy or high-risk.  Despite this seemingly high score, this model predicted healthy loans with a FPR of 0.5% but had a 9% FPR when predicting high-risk loans.  The ramifications of nearly 10% high-risk loans initially categorized as healthy loans may have detrimental impact to the lender.   Given the imbalance of healthy loans versus high-risk loans in constructing the prediction model, the RandomOverSampler from the imbalance-learn library was implemented.

Using the RandomOverSampler, the FPR was maintained at 0.5% for healthy loan prediction but was dramatically reduced from 9% to 0.5% for high-risk loans.  From the lender’s perspective, predicting a high-risk loan from just 7 metrics with over 99% precision would be beneficial overall to the lender’s business.  Since the precision of predicting high-risk loans using the model constructed using RandomOverSampler is much higher than that without, it is recommended that this model be used by the lender to address risk assessment of a borrower’s loan. 
