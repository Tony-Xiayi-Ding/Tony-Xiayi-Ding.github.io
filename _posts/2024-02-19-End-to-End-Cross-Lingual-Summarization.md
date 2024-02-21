---
layout: post
title: End-to-End Cross-Lingual Summarization with Multilingual Pre-training
subtitle: Excerpt from project report
gh-repo: daattali/beautiful-jekyll
cover-img: /assets/img/Text-Summarization.jpg
thumbnail-img: /assets/img/Text-Summarization.jpg
share-img: /assets/img/Text-Summarization.jpg
tags: [Python, Deep Learning, NLP, Transformer, CLS]
comments: true
---

STAY TUNED!!!

## Abstract
Cross-lingual summarization (CLS) generates summaries in a target language from texts in a source language, serving as a valuable tool in cross-cultural and global communications. Traditionally achieved through a pipeline of machine translation (MT) and monolingual summarization (MS), CLS tasks are increasingly being explored with various end-to-end mode frameworks without the intermediate outputs. Building on the latest work on end-to-end CLS, we adopt two different approaches to integrating multilingual pre-training into generating Chinese summaries from English source texts: 1) using pre-trained multilingual embeddings only from the translation model mBART, and 2) fine-tuning the entire mBART model on CLS data. The second approach significantly outperforms the baseline model and the first approach, achieving a ROUGE-1 score of 22.37 on the in-distribution evaluation data and 3.82 on an external dataset. These scores surpass the baseline transformer model by 932% and 5,357%, and the first model by 1,002% and 3,720%, respectively.

## Data
We train all our models on the [EN2ZHSUM](https://drive.google.com/file/d/1GZpKkHnTH_1Wxiti0BrrxPm18y9rTQRL/view){: target="_blank" rel="noopener noreferrer"} dataset from, contributed by [Zhu et al.](https://arxiv.org/abs/1909.00156){: target="_blank" rel="noopener noreferrer"} with paired English texts and Chinese summaries. The dataset was constructed by first obtaining news articles and their corresponding highlights as sources and targets for monolingual summarization, then using a "round-trip" strategy to translate the summaries to the target language then back to the source language. The translation results were then evaluated using ROUGE to only include the results with high quality in the final dataset. The corpus of EN2ZHSUM contains 370,759 CLS pairs.


For model evaluation, in addition to the test set of EN2ZHSUM, we also use [ClidSum](https://github.com/krystalan/ClidSum?tab=readme-ov-file){: target="_blank" rel="noopener noreferrer"}, developed by [Wang et al.](https://aclanthology.org/2022.emnlp-main.526/){: target="_blank" rel="noopener noreferrer"}, to assess the models' suitability to be generalized to out-of-distribution dataset. Vastly different from EN2ZHSUM, ClidSum consists of more than 67,000 dialogues and 112,000 annotated summaries. As a result, ClidSum presents an alternate text medium to assess the performance of our models on general CLS tasks. Due to the issue of data availability and the constraint of computing resources, for evaluation we only use 1,000 samples from [XMediaSum40k](https://drive.google.com/file/d/1ETwdHFKEp-DZYLejHvoMp3CXn-kTsmoB/view){: target="_blank" rel="noopener noreferrer"}, which is a subset of ClidSum that contains media interviews and their summaries. 

## Methods


## Results


## Conclusion


## References

