# Credit Risk Classification

## Overview of the Analysis

This analysis, conducted using Python, looks at data from 77,536 loans and constructs a prediction model determining the likelihood a loan will be healthy or one of high-risk and close to defaulting.  A total of seven factors were considered: (1) loan amount, (2) interest rate, (3) borrower’s income, (4) borrower’s debt to income ratio, (5) number of accounts under borrower's name at the time of the loan, (6) number of derogatory marks on the borrower’s loan report, and (7) borrower’s total debt.

A linear logistic regression model from the SKLearn library was instantiated, the original data was split (75% went to training, 25% went to testing), and the model was trained and tested to assess its accuracy at predicting healthy versus high-risk loans.  Additionally, a second prediction model using the imbalanced-learn library's RandomOverSampler module was constructed to assess the effects of the inherent lopsidedness within the original dataset (2,500 high-risk loans versus 75,036 healthy loans).


## Results

 ### **Machine Learning Model 1 (original data)**:
  * overall accuracy score = 99%
  * overall balanced accuracy score = 95% (difference from overall accuracy score indicative of varying sample sizes)

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

### **Machine Learning Model 2 (RandomOverSampler):**
  * overall accuracy score = 99%
  * overall balanced accuracy score = 99%
  
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

The logistic regression model using the original data had an overall balanced accuracy score of 95%  prediciting a loan's fate as either healthy or high-risk.  Although prediction of healthy loans had a false positivity rate (FPR) of 0.5%, a 9% FPR occurred when predicting high-risk loans (refer to the comments within the code to see how FPR was calculated).  The ramifications of mispredicting nearly one out of ten high-risk loans as healthy may potentially lead to considerable negative effects for the lender.   Given the imbalance of healthy loans versus high-risk loans in constructing the prediction model, however, unfairness may occur, thus, the RandomOverSampler module was implemented to observe the consequence of this potential bias.

Using the RandomOverSampler, the FPR was maintained at 0.5% for healthy loan prediction but was 0.5% for high-risk loans, a sizeable decrease from the previous 9%.  From the lender’s perspective, predicting a high-risk loan from just 7 metrics with over 99% precision would be beneficial and minimizes the instances of predicting high-risk loans as healthy.  However, the RandomOverSampler primarily illustrates that bias is present in the construction of Machine Learning Model 1 (model based solely on original data).  The RandomOverSampler is speculative as it is based on previous data and not real or new data.  In fact, the RandomOverSampler may just repeat previous data points in order to establish a sample size more aligned to that of the majority class (the healthy loans).  So while the RandomOverSampler model is more precise at predicting high-risk loans, it should be understood that this model is not based on real world data.  Ideally, more real world data regarding high-risk loans should be used to correct for the data imbalance ultimately leading to validation of the prediction model. But in the absence of new data, one, the RandomOverSampler may be used but should be done knowing its inherent caveats, two, other models such as constructing a prediction model that under-samples the healthy loans to balance the dataset should be used in conjunction to lend further creedence and to glean more insight into the efficacy of the prediction model. 
