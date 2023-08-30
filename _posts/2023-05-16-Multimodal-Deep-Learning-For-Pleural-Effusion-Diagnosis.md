---
layout: post
title: Multimodal Deep Learning for Pleural Effusion Diagnosis
subtitle: Excerpt from project report
gh-repo: daattali/beautiful-jekyll
cover-img: /assets/img/COVID.jpeg
thumbnail-img: /assets/img/COVID.jpeg
share-img: /assets/img/COVID.jpeg
tags: [Python, Deep Learning, Computer Vision, NLP, MIMIC-CXR]
comments: true
---


**Abstract**

Chest X-rays are among the most commonly ordered imaging tests. Applying deep learning techniques to X-ray images is a typical application of computer vision in healthcare. Nevertheless, using X-ray images alone does not always lead to generalizable model performances. Combining patients’ clinical reports, which contain rich and important patient diagnostic information, with X-ray images could give the model more information for prediction. Consequently, this project will be focusing on deriving and examining the best fusion strategies for implementing a multimodal approach with regard to pleural effusion prediction. Using X-ray images and clinical text reports, we mainly combined VGG16 with DistilBERT to better predict the presence of pleural effusion. Two sets of fusion strategies are proposed, namely early fusion, where we concatenate the learned vector representations of images and texts before classification, and late fusion, where we leverage the predicted probabilities from the two modalities. Ultimately, we found that the late fusion multimodality model with an elastic net regularized logistic regression model achieved the best overall performance, with an AUC value of 0.9887. On the other hand, the early fusion strategy achieved inferior results, which indicates that the early fusion strategy that we utilized here is not specifically suitable for integrating X-ray images with clinical text data.

**Data**

- MIMIC-CXR Database v2.0.0
  - X-ray images in DICOM files
  - Contains clinical reports
- MIMIC-CXR-JPG Database v2.0.0
  - X-ray images in JPG files
- 5.5 TB in total size
  - Due to the large size of the files and limitations of computing power, we eventually only used about 10% of the entire dataset


**Results**

![CV_Results](/assets/img/PE_IMG1.png)

![Model_Interpretability](/assets/img/PE_SM_GradCAM.png){: .mx-auto.d-block :}

For our baseline imaging model, the VGG16-based CNN with data augmentation, it ultimately achieved a test accuracy of 84.92% and an AUC of 0.9099. Nevertheless, this model consistently overfitted on the training data, regardless of the application of data augmentation techniques, as shown in Figure 1a. Consequently, this indicates that this model lacks a good generalizability to unseen data beyond the overfitting point.

Furthermore, for our early fusion approach towards our multimodality model, the validation accuracy appeared to plateau at around 81%, even under elongated training time, as shown in Figure 1b. This suggests that the early fusion strategy may not be fully capitalizing on the potential synergies between the features of the X-ray images and the clinical texts to maximize the predictive accuracy. Ultimately, this early fusion strategy achieved an AUC of 0.8791, which is slightly worse than that of our baseline model.

Our late fusion strategy achieved much more success compared to the aforementioned baseline approach and the early fusion multimodality model. To elaborate, a simple averaging of the predicted probability values from both models resulted in an AUC of 0.9804. For the regression-based late fusion approaches, by implementing a linear regression using the predicted probabilities, we were able to achieve an AUC of 0.9817. Remarkably, when we applied a logistic regression model with elastic net regularization, the AUC further increased to 0.9887, which is also our highest AUC value among all approaches and models. These results underline the effectiveness of late fusion multimodal learning in harnessing the predictive potential of both X-ray images and clinical reports for superior model performances.

This interactive visualization uses a Python-based app framework called **streamlit** to demonstrate COVID-19 cases, deaths, and vaccinations data in US by states. This visualization also allows you to check out the geographical distribution and the temporal evolution of the case fatality rates and the total vaccinations per hundred people for various states at different time points. The data for this visualization were obtained from the [New York Times](https://github.com/nytimes/covid-19-data/blob/master/us-counties-2021.csv) and [Our World in Data](https://github.com/owid/covid-19-data/blob/master/public/data/vaccinations/us_state_vaccinations.csv).

Click on the visualizaiton below to play with it!

[![COVID_viz](/assets/img/COVID_Viz.png 'COVID_Viz')](https://tony-xiayi-ding-covid-19-visualizations-streamlit-app-kxppyx.streamlit.app/)

You can also click **[here](https://tony-xiayi-ding-covid-19-visualizations-streamlit-app-kxppyx.streamlit.app/)** to access the interactive visualization.

