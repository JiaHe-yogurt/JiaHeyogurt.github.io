---
permalink: /aggregateevaluation/
title: "Aggregate Evaluation"
author_profile: true
redirect_from: 
  - /md/
  - /markdown.html
---
Sometimes you have the same model evaluated on multiple independent dataset, you may want to make conclusion based on all those result instead of a single result which can be biased.
We adopt the concept of micro and micro scores to aggregated multiple results. Please refer to this [post](https://towardsdatascience.com/micro-macro-weighted-averages-of-f1-score-clearly-explained-b603420b292f#2f35) to understand how they work. In our context, the  macro precision/recall/F1-score is computed using the arithmetic mean (aka unweighted mean) of all the per-result precision/recall/F1-scores. Micro score computes a global average F1 score by counting the sums of the True Positives (TP), False Negatives (FN), and False Positives (FP).



## Data Schema
* Micro/Macro scores. A list of dictionaries of independent evaluation results from the same model.

  * result1 = {'TP': 1, 'FP': 1, 'FN': 0,  'precision': 0.5, 'recall': 1.0, 'F1': 0.667}

  * result2 = {'TP': 1, 'FP': 1, 'FN': 1,  'precision': 0.5, 'recall': 0.5, 'F1': 0.5}

