---
layout: post
title: Diabetes Readmission Prediction
subtitle: Excerpt from project report
gh-repo: daattali/beautiful-jekyll
cover-img: /assets/img/diabetes.jpeg
thumbnail-img: /assets/img/diabetes.jpeg
share-img: /assets/img/diabetes.jpeg
tags: [Python, Machine Learning]
comments: true
---


    Diabetes is a common health condition, and those who were diagnosed with diabetes have to monitor their blood sugar levels for an extensive amount of time, usually their whole lives. If not well-managed, individuals may be admitted to healthcare facilities. In addition, hospital readmissions due to diabetes within 30 days may indicate that the patient is especially at risk of medical complications. Numerous predictive models had been built to predict hospital readmission; nevertheless, no previous studies had audited the predictive models for bias regarding hospital readmission. 
    
    As a result, this paper aims to explore predictive models for the readmission of diabetic patients as well as to determine if there are any potential biases in the decision-making processes of these models. By applying models such as logistic regression, XGBoost, and random forest, we found that model designs for building a predictive program on a diabetes hospital readmissions dataset can indeed introduce a certain amount of bias. It was also found that there were more Caucasian patients being readmitted to the hospital than actually needed, and non-Caucasian patients who should be readmitted to the hospital are not predicted by the models to experience readmittance as often compared to Caucasian patients. Furthermore, by comparing the XGBoost and random forest models, the XGBoost models tend to have more equitable predictions while still maintaining comparable predictive ability.


## Models and their performances


### Logistic Regression


### XGBoost


### Random Forest



## Additional Evaluations

Shapley values for the XGboost model trained on the original dataset:

![Shapley_Value](/assets/img/Shapley_Values.png){: .mx-auto.d-block :}

Feature importance for the random forest model trained on the original dataset:

![Feature_Importance](/assets/img/Feature_Importance.png)



## Conclusions and Discussion

????



**FYI:**

  -The manuscript for this project can be accessed through this [link](/assets/pdf/Diabetes_Readmission_Prediction.pdf).

  -You can also click this [link](https://colab.research.google.com/drive/1MZb4R1nWX-qvdsH-_v-HjSxYEhjN6Yxx?usp=sharing) to access this project's Colab Notebook.


