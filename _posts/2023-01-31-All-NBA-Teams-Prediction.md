---
layout: post
title: All-NBA Teams Selection Prediction
subtitle: Excerpt from project report
gh-repo: daattali/beautiful-jekyll
cover-img: /assets/img/NBA.jpg
thumbnail-img: /assets/img/NBA.jpg
share-img: /assets/img/NBA.jpg
tags: [R, Machine Learning, NBA]
comments: true
---


Every year, there are more than 450 basketball players that play in a single NBA season, but only 15 of them would get selected into the All-NBA teams for that specific season. As a huge NBA fan, it makes me wonder what makes these 15 players stand out from all the NBA players. As a result, this project will be trying to locate the top features of an NBA player that are indicative of All-NBA teams selection, and to what extent can I predict the selection of All-NBA team using the players’ statistics?
    
A total of two datasets were used in this project, namely *Seasons_Stats.csv* and *All.NBA.1984-2018.csv*. These two datasets were all originally parsed from a website called [Basketball Reference](https://www.basketball-reference.com/).

- The Seasons_Stats.csv file can be accessed through this [link](https://www.kaggle.com/datasets/drgilermo/nba-players-stats?select=Seasons_Stats.csv). This dataset contains players’ game statistics from year 1950 to 2017, and each column represents an attribute of that player. These attributes include basic statistics such as games played (G) and total points scored in that season (PTS) as well as the more advanced metrics such as Win Shares (WS), which is an estimate of the number of wins contributed by that player.

- The All.NBA.1984-2018.csv file can be accessed through this [link](https://www.kaggle.com/code/kerneler/starter-all-nba-players-1984-2018-e8f3592a-1/data?select=All.NBA.1984-2018.csv). This dataset contains all the players that are selected to be in All-NBA teams starting from the 1984-1985 season to the 2016-2017 season. One thing to note is that before the 1988-1989 season, only 2 teams of All-NBA teams were selected each year; and starting from the 1988-1989 season, a total of 3 teams of All-NBA teams were selected each year.

**FYI:**
- **Please click this [link](https://tony-xiayi-ding.github.io/BST260-Final-Project/) to read the entire project.**

## Models Used
- **Please click this [link](https://tony-xiayi-ding.github.io/BST260-Final-Project/) to read the entire project.**


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





