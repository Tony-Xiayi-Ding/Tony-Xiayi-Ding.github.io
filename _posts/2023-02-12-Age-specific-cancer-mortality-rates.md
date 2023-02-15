---
layout: post
title: Age-specific Cancer Mortality Rates
subtitle: An interactive visualization
gh-repo: daattali/beautiful-jekyll
cover-img: /assets/img/diabetes.jpeg
thumbnail-img: /assets/img/diabetes.jpeg
share-img: /assets/img/diabetes.jpeg
tags: [Python, Interactive Visualization, Healthcare]
comments: true
---

By cleaning a [cancer mortality dataset](https://github.com/hms-dbmi/bmi706-2022/blob/main/cancer_data/cancer_ICD10.csv) and merging it with a [population dataset](https://github.com/hms-dbmi/bmi706-2022/blob/main/cancer_data/population.csv), I created an interactive visualization using a Python-based app framework called **streamlit** to demonstrate the age-specific cancer mortality rates in different countries. This visualization also allows you to check out the mortality rate of various kinds of cancers for different countries, years, and genders. 

Click on the visualizaiton below to play with it!

[![Cancer_viz](/assets/img/Cancer_Viz.png 'Cancer_Viz')](https://tony-xiayi-ding-bmi706-2023-ps3-streamlit-app-bg5nwe.streamlit.app/)

You can click **[here](https://tony-xiayi-ding-bmi706-2023-ps3-streamlit-app-bg5nwe.streamlit.app/)** to access the interactive visualization.


### Logistic Regression

ROC curves for logistic regression models with L2 and L1 penalizations:

![Cancer_Viz](/assets/img/Cancer_Viz.png)

The performance of our baseline logistic regression model was considered poor as we derived an AUC score of around 0.5(0.5054 for L2-penalized and 0.5032 for L1-penalized). Though the accuracy of this model was high at 0.89, it was solely due to the fact that the model was trying to predict every instance to be a negative label, which also happened to be the dominating label in our datasets, including the test set.

### Random Forest

ROC curves for random forest models trained on the original dataset, oversampled dataset, and undersampled dataset respectively from left to right:

![RF_ROC](/assets/img/Random_Forest_ROC_Curves.png)

For the random forest models trained using the original dataset and the undersampled dataset, we achieved AUC scores of 0.651 when evaluated on a test set. However, for the random forest model trained using an oversampled dataset, the AUC score went down to 0.598.

### XGBoost

ROC curves for XGBoost models trained on the original dataset, oversampled dataset, and undersampled dataset respectively from left to right:

![XGB_ROC](/assets/img/XGBoost_ROC_Curves.png)

Lastly, for XGBoost, the highest AUC score, 0.638, was achieved by the model trained on the original dataset, followed by the model trained on the undersampled dataset with an AUC score of 0.636. The model trained on the oversampled dataset had the lowest AUC score of 0.566 among the three XGBoost models.


## Additional Model Evaluations

Because machine learning models like random forest and XGBoost are difficult to interpret, we hope to distinguish the bias using feature importance for the random forest model and SHAP/Shapley values for the XGBoost model to better understand our models’ decision making processes.

Shapley values for the XGboost model trained on the original dataset:

![Shapley_Value](/assets/img/Shapley_Values.png){: .mx-auto.d-block :}

Feature importance for the random forest model trained on the original dataset:

![Feature_Importance](/assets/img/Feature_Importance.png)


For the random forest model without oversampling or undersampling, the precision is the lowest for Caucasians, followed by African Americans, and finally other races. The recall is exactly the reverse: Caucasians have the highest recall, followed by African Americans, and finally other races. When looking at recall, we could see African American patients as well as patients of other races usually have a relatively lower recall than Caucasian patients. Based on the definitions of precision and recall, we can interpret our findings as:

- **There were more Caucasian patients being readmitted to the hospital than actually needed(i.e. there are more false positives for Caucasian patients)**. 

- **Non-Caucasian patients who should be readmitted to the hospital are not predicted by the model to experience readmittance as often compared to Caucasian patients(i.e. more false negatives for non-Caucasian patients)**. 
    - For this situation, however, it is more beneficial to err on having higher false positives, rather than higher false negatives. This is because we would prefer to provide patients with additional resources who may not necessarily need them, rather than missing any patients that would actually need additional medical assistance.









