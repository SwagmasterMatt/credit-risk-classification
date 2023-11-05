# credit-risk-classification

# Module 12 Report

## Overview of the Analysis


* In this analysis, we examined the efficacy of two machine learning models on financial data, with the intent to predict the risk associated with loans
* (image.png) Our aim was to predict the loan status outcome using the following data points from the financial institute.
* The goal was to determine whether loans were likely to be high-risk or healthy (low-risk), which is critical in the financial sector for risk management and decision-making processes. We examined various predictive variables and generated 2 models to understand the distribution of risk across loans.
* Among the original data, there were 75036 healthy loans and 2500 high risk loans identified. This likely involved a lot of manual labor hours to conclude.
* The analysis involved preprocessing data, selecting features, training the models, and evaluating their performance. We applied logistic regression as the base classifier and explored the effect of resampling to address class imbalance in the dataset.
* The majority of results fell under class 0 - Healthy loans which caused an imbalance in calcuations. Model 2 attempts to correct that with resampling so that the distribution is less bias towards healthy loans.

## Results


The performance of the machine learning models is summarized as follows:

* Machine Learning Model 1 (Without Resampling):
  * Balanced Accuracy Score: Approximately 0.952
  * Confusion Matrix: [11863 True Negatives, 1023 False Positives; 56 False Negatives, 5613 True Positives]
  * Classification Report:
    * Precision for healthy loans (class 0): 1.00
    * Recall for healthy loans (class 0): 0.99
    * F1-score for healthy loans (class 0): 1.00
    * Precision for high-risk loans (class 1): 0.85
    * Recall for high-risk loans (class 1): 0.91
    * F1-score for high-risk loans (class 1): 0.88



* Machine Learning Model 2 (With Oversampling):
  * Balanced Accuracy Score: Approximately 0.939
  * Confusion Matrix: [11849 True Negatives, 1161 False Positives; 4 False Negatives, 6151 True Positives]
  * Classification Report:
    * Precision for healthy loans (class 0): 1.00
    * Recall for healthy loans (class 0): 0.99
    * F1-score for healthy loans (class 0): 1.00
    * Precision for high-risk loans (class 1): 0.84
    * Recall for high-risk loans (class 1): 0.99
    * F1-score for high-risk loans (class 1): 0.91


## Summary

Summarize the results of the machine learning models, and include a recommendation on the model to use, if any. For example:
* Model 1: The logistic regression model demonstrates a strong predictive capability for both healthy (class 0) and high-risk (class 1) loan labels. For healthy loans, it achieves perfect precision and recall (both 1.00), indicating exceptional performance in correctly classifying these cases without false positives or negatives. For high-risk loans, the model's precision is 0.85, meaning that when it predicts a loan to be high risk, it is correct 85% of the time. Its recall is 0.91, capturing 91% of all actual high-risk loans.

    However, the model underclassifies high-risk loans by 15%, which could be critical depending on the business context. For instance, the cost associated with misclassifying a high-risk loan as healthy could be substantial if that loan defaults. Thus, while the model is robust, the business implications of these misclassifications must be considered. In particular, it may be necessary to adjust the model's threshold for predicting high-risk loans or to incorporate this model's predictions into a larger decision-making framework that also considers the potential monetary risk to the company.

    In summary, the logistic regression model is highly accurate overall but does exhibit a tendency to underclassify high-risk loans. The acceptability of this range would depend on the specific financial thresholds and risk appetites of the company using the model.

* Model 2: After accounting for the oversampling the results are much more balanced with the recall increasing to 99% for Class 1. The precision for class 1 has gone down by 1%. For a business sense this means that the model is likely to classify a healthy loan as high risk but will very rarely classify a high risk loan as healthy. This is a desireable tradeoff in a "better safe than sorry" scenario. The capital implications is "profit lost due to incorrect classification" versus "debt gained via default due to underclassifcation"


    There is little to no change in the predictions for class 0 after utilizing the oversampling which means we maintain our high performing predictions of the majority class.
## Recommendation 

* Model 2 is going to provide much better incentive for the business and will also mitigate risk. While we had a slight increase in false positve (healthy classified as high risk), we generated a tradeoff of 54 less false negatives (high risk loans classified as healthy).

* Over the entire data set of 77536, only 13 would have been False Negatives with a total default risk sum of $129500 - This value can be directly compared to cost saving measures after implementing the model. This number serves purely as a theoretical gesture since in a real scenario the business would not know the difference in a false versus true identification without further investigation.

* Further studies should be implemented by the business to compare its own manual accuracy rate to determine which loans were actually defaulted on - it is possible that the model is more accurate than human evaluation of the risk and false positives are actually true positives.