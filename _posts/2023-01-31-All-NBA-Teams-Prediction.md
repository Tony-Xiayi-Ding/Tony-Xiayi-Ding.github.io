---
layout: post
title: All-NBA teams Selection Prediction
subtitle: Excerpt from project report
gh-repo: daattali/beautiful-jekyll
cover-img: /assets/img/diabetes.jpeg
thumbnail-img: /assets/img/diabetes.jpeg
share-img: /assets/img/diabetes.jpeg
tags: [R, Machine Learning, NBA]
comments: true
---


Diabetes is a common health condition, and those who were diagnosed with diabetes have to monitor their blood sugar levels for an extensive amount of time, usually their whole lives. If not well-managed, individuals may be admitted to healthcare facilities. In addition, hospital readmissions due to diabetes within 30 days may indicate that the patient is especially at risk of medical complications. Numerous predictive models had been built to predict hospital readmission; nevertheless, no previous studies had audited the predictive models for bias regarding hospital readmission. 
    
As a result, this project aims to explore predictive models for the readmission of diabetic patients as well as to determine if there are any potential biases in the decision-making processes of these models. By applying models such as logistic regression, XGBoost, and random forest, we found that model designs for building a predictive program on a diabetes hospital readmissions dataset can indeed introduce a certain amount of bias. It was also found that there were more Caucasian patients being readmitted to the hospital than actually needed, and non-Caucasian patients who should be readmitted to the hospital are not predicted by the models to experience readmittance as often compared to Caucasian patients. Furthermore, by comparing the XGBoost and random forest models, the XGBoost models tend to have more equitable predictions while still maintaining comparable predictive ability.

**FYI:**

- **The manuscript for this project can be accessed through this [link](/assets/pdf/Diabetes_Readmission_Prediction.pdf).**

- **You can also click this [link](https://colab.research.google.com/drive/1eioghlOmz1_r8cVeEASUk_DKY2ar9dpd?usp=share_link) to access this project's Colab Notebook.**

## Models


### Logistic Regression

ROC curves for logistic regression models with L2 and L1 penalizations:

![LGR_ROC](/assets/img/Logistic_Regression_ROC_Curves.png)

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


## Conclusion and Discussion

Through our exploration of model performance metrics and analysis of various machine learning algorithms, we found that model designs for building a predictive program on a diabetes hospital readmissions dataset can introduce a certain amount of bias. Overall, the models presented less-than-desirable predictive performance, and different degrees of bias were observed depending on the model design. Comparing the XGBoost and random forest models, the XGBoost models tend to have more equitable predictions while still maintaining comparable predictive ability. Preprocessing methods, such as oversampling and undersampling, were used to correct data imbalances and deficiencies, and these methods affected not only the predictive capabilities of these models but also the level of bias that propagated in the predictions. Overall, we assessed the bias of decision-making within these models, which has not been done in previous studies that built machine learning models for this dataset. 

For random forest, we concluded from the metrics that the model presents predictive bias among races but no bias regarding genders. The feature importance for Caucasians is higher than African Americans, which is in turn higher than other races. On the contrary, though the feature importance for males is higher than that for females, the difference between the two is relatively small. Nevertheless, overall, the differences in feature importance values are small, which makes it hard for us to validate the significance of the bias based on feature importance only. For XGBoost, our conclusion was no bias existence. In alignment with our conclusion, race or gender is not one of the top ten most important features according to Shapley values.

Lastly, there remain a few limitations to this project as well. To be specific, we did not provide statistical proof of the existence of bias since it was hard to validate the statistical significance of the differences between model performance metrics for different populations given the models’ generally poor performances on this imbalanced dataset. Hence, we resorted to Shapley values and feature importance tables to buttress our observations and findings. In addition, we removed quite a few instances and features due to missing values, which also meant that we lost a certain amount of prediction power for our models since the values for those features and instances were not completely empty. Future research could focus on improving the model performances by either using superior sampling and imputation techniques or overall better models. Future research could also attempt to provide statistical evidence to mathematically prove the existence of bias within the models for populations with certain characteristics. 


## References

Alturki, L., Aloraini, K., Aldughayshim, A., & Albahli, S. (2019, November). Predictors of readmissions and length of stay for diabetes related patients. In 2019 IEEE/ACS 16th International Conference on Computer Systems and Applications (AICCSA) (pp. 1-8). IEEE.

Beata Strack, Jonathan P. DeShazo, Chris Gennings, Juan L. Olmo, Sebastian Ventura, Krzysztof J. Cios, and John N. Clore, “Impact of HbA1c Measurement on Hospital Readmission Rates: Analysis of 70,000 Clinical Database Patient Records,” BioMed Research International, vol. 2014, Article ID 781670, 11 pages, 2014

Centers for Disease Control and Prevention. National diabetes statistics report, 2017. Centers for Disease Control and Prevention website. www.cdc.gov/diabetes/pdfs/data/statistics/national-diabetes-statistics-report.pdf. Updated July, 18 2017. Accessed December 11, 2022.

MIT 6.3950/6.3952 (September 2022) Lecture_3_Healthcare, Slide 24 and Slide 28

Rubin DJ. Hospital readmission of patients with diabetes. Curr Diab Rep. 2015 Apr;15(4):17. doi: 10.1007/s11892-015-0584-7. Corrected and republished in: Curr Diab Rep. 2018 Mar 13;18(4):21. PMID: 25712258.

Shang, Y., Jiang, K., Wang, L., Zhang, Z., Zhou, S., Liu, Y., Dong, J., & Wu, H. (2021). The 30-days hospital readmission risk in diabetic patients: predictive modeling with machine learning classifiers. BMC medical informatics and decision making, 21(Suppl 2), 57. https://doi.org/10.1186/s12911-021-01423-y

Suresh, A. (2021, June 22). What is a confusion matrix? Medium. Retrieved December 12, 2022, from https://medium.com/analytics-vidhya/what-is-a-confusion-matrix-d1c0f8feda5 





