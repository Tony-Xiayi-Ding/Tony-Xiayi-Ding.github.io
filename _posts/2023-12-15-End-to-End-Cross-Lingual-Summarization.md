---
layout: post
title: End-to-End Cross-Lingual Summarization with Multilingual Pre-training
subtitle: Excerpt from project report
gh-repo: daattali/beautiful-jekyll
cover-img: /assets/img/Pleural_Effusion_new.jpeg
thumbnail-img: /assets/img/Pleural_Effusion.jpeg
share-img: /assets/img/Pleural_Effusion.jpeg
tags: [Python, Deep Learning, NLP, Transformer, CLS]
comments: true
---


## Abstract
Chest 


**FYI:**

- **The manuscript for this project can be accessed through this [link](/assets/pdf/Pleural_Effusion_Multimodal_Deep_Learning.pdf){: target="_blank" rel="noopener noreferrer"}.**

- **You can also click this [link](https://docs.google.com/presentation/d/1b0KqUYQFOT9HYibQCC77nqMCveSSe9pHJa5vpG1ZnjI/edit?usp=sharing){: target="_blank" rel="noopener noreferrer"} to check out the short presentation slides that I made for this project.**


## Data
- MIMIC-CXR Database v2.0.0
  - X-ray images in DICOM files
  - Contains clinical reports


## Results

For our baseline imaging model, the VGG16-based CNN with data augmentations, it ultimately achieved a test accuracy of 84.92% and an AUC of 0.9099. Nevertheless, this model consistently overfitted on the training data, regardless of the application of data augmentation techniques, as shown in the Figure below. Consequently, this indicates that this model lacks a good generalizability to unseen data beyond the overfitting point.

![Accuracy_Evolution](/assets/img/PE_AccuracyPlot.png){: .mx-auto.d-block :}

Furthermore, for our early fusion approach towards our multimodality model, the validation accuracy appeared to plateau at around 81%, even under elongated training time, as shown in Figure 1b. This suggests that the early fusion strategy may not be fully capitalizing on the potential synergies between the features of the X-ray images and the clinical texts to maximize the predictive accuracy. Ultimately, this early fusion strategy achieved an AUC of 0.8791, which is slightly worse than that of our baseline model.

Our late fusion strategy achieved much more success compared to the aforementioned baseline approach and the early fusion multimodality model. To elaborate, a simple averaging of the predicted probability values from both models resulted in an AUC of 0.9804. For the regression-based late fusion approaches, by implementing a linear regression using the predicted probabilities, we were able to achieve an AUC of 0.9817. Remarkably, when we applied a logistic regression model with elastic net regularization, the AUC further increased to 0.9887, which is also our highest AUC value among all approaches and models. These results underline the effectiveness of late fusion multimodal learning in harnessing the predictive potential of both X-ray images and clinical reports for superior model performances.

Here is a summary of all the results mentioned above:

![Results_Summary](/assets/img/PE_IMG1.png){: .mx-auto.d-block :}

Lastly, to interpret our vision network, we employed two gradient-based methods: saliency maps and GradCAM, shown in the Figure below. Both techniques utilize gradients to identify important regions within an image. Saliency maps calculate the gradient of the network's loss with respect to the input image and visualize these gradients as a heatmap (Simonyan et al., 2013). GradCAM, on the other hand, calculates gradients only for the last convolutional layer before the global pooling operation, resulting in a more abstract representation of input-output relationships and providing a different perspective on the network's underlying mechanisms (Selvaraju et al., 2017). 

![Model_Interpretability](/assets/img/PE_SM_GradCAM.png){: .mx-auto.d-block :}

Both methods above highlighted similar regions. In addition, aside from the lung areas, the model sometimes pays attention to other regions as well as medical devices. While this could be advantageous for diagnosis, it is not ideal for model interpretability because the model’s focus is not solely on disease locations and related pathologies.

## Conclusion

Overall,

## References

Johnson, A., Lungren, M., Peng, Y., Lu, Z., Mark, R., Berkowitz, S., & Horng, S. (2019). MIMIC-CXR-JPG - chest radiographs with structured labels (version 2.0.0). PhysioNet. https://doi.org/10.13026/8360-t248.

Sanh, V., Debut, L., Chaumond, J., & Wolf, T. (2019). DistilBERT, a distilled version of BERT: smaller, faster, cheaper and lighter. arXiv preprint arXiv:1910.01108.

Selvaraju, R. R., Cogswell, M., Das, A., Vedantam, R., Parikh, D., & Batra, D. (2017). Grad-cam: Visual explanations from deep networks via gradient-based localization. In Proceedings of the IEEE international conference on computer vision (pp. 618-626).

Simonyan, K., Vedaldi, A., & Zisserman, A. (2013). Deep inside convolutional networks: Visualising image classification models and saliency maps. arXiv preprint arXiv:1312.6034.

