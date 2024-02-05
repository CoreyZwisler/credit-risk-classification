# Credit Risk Analysis Report

</br>

## Overview of the Analysis

* The purpose of this analysis is to look at the past history of borrowers and create a Machine Learning model to predict the credit worthiness of borrowers. This will allow lending providers to assess whether or not a borrow is at high risk of not being able to pay back the money they borrowed.

</br>

* The data I am using to make these predicitions is from the `lending_data.csv` provided. After converting it into a dataframe, I can see that the data provides useful information including: the size of the loan, the interest rate, the borrower's yearly income, the debt-to-income ratio, how many accounts the borrower has, the number of deragatory marks the borrow has, their total debt, and the status of the loan (`healthy[0]`, `high_risk[1]`).

  * Using this data, I am trying to predict the odds of a loan being healthy (`loan_status`) using the rest of the provided data.

* The steps used are similar for each model used. 
  
  1. After importing the data, I split it into 2 variables: `y` being the `loan_status` column and `X` as the rest of the data.

  2. I then split the data into test and train sets for the purpose of training the model.

  3. I created a regression model snd fit it using the training data created from the previous step.

  4. I then created predictions using `.predict` on the created regression model.

  5. Finally, I evaluated the model using `accuracy_score`, `confusion_matrix`, and `classification_report`.

  6. The resampled model follows the same steps. but with a resampled data set created using `RandomOverSample`.

    * The resampled model is important to view in this situation because the `high_risk` data is severely under-represented in the data set.

</br>

## Results

* Machine Learning Model 1:
  
  * The model had an accuracy score of 95.2%

  * It had a precision score of 100% with a 1% recall error for the `0` loans.

  * The `1` loans had a precision score of 85% with a 9% recall error.

* Machine Learning Model 2:
  
  * The resampled model had an accuracy score of 99.4%.

  * It had a precision score of 100% with a 1% recall recall error for the `0` loans.

  * The `1` loans had a precision score of 84% with a 1% recall error.

</br>

## Summary

If you do not recommend any of the models, please justify your reasoning.

* After analyzing the results from both models, I would recommend using Model 2. 

* My reasoning for this is because this model generated fewer false positives for the `1` loans while maintaining a high accuracy score. This is important because we don't want the model saying that a loan is healthy when it is in fact, not healthy. 

  * Model 2 represented this well by only generating 4 false positives for the `1` loans, where as Model 1 generated 56.

  * While model 2 did generate more false negatives for the `0` loans, 116 as opposed to 102 from Model 1, I believe this is an acceptable margin of error since the the amount of false positives for the `1` loans is significantly larger.

</br>