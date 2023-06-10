---
permalink: /
title: "Anomaly-Detection-Model-Evaluation is a python package that provides a variaty of metrics to evaluate anomaly detection models."
excerpt: "About me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---
Evaluation for time series anomaly detection (TSAD) models is a challenging yet understudied problem. TSAD models have different properties that represent model capability, and there are different approaches for evaluation based on application and business need. However, there is limited package for a systematic TSAD model evaluation. Anomaly-Detection-Model-Evaluation is a python package that provides a variety of evaluation metrics, including point-wise, segment-wise evaluation, root cause analysis and aggregate evaluation. 

# Installation & Import

Anomaly-Detection-Model-Evaluation is supported across Windows, Mac and Linux on Python 3.0+.


<pre>
pip install Package-name
from Package-name import functions
</pre>

# Getting started

Anomaly-Detection-Model-Evaluation targets at evalutating models performance only, it requires true label and output from any model. You should use their own tool for model training. To use the metrics, you need to set some metric configurations, which will be introducted in the following section. 

## Terminology
We define terms that we will use throughout the document.

| Term | Definition |
|:--------|:-------:|
| True Position (TP)  |   |
| True Negative (TN)  |  |

## Data Schema
------
Each evaluation metric may require different input. We examplify the input format for each metric here, and introduce metrics in detail in separate pages.

### Point-wise/Segment-wise unadjusted/adjusted score
* True label (pd.DataFrame)

| TimeStamp | label | rootcause |
|:--------|:-------:|--------:|
| 2023-03-29 00:56:00   | 0 | NaN   |
| 2023-03-29 00:56:00   | 1 | Cpu pressure   |

* Predicted label (pd.DataFrame)

| TimeStamp | label | 
|:--------|:-------:|
| 2023-03-29 00:56:00   | 0 | 
| 2023-03-29 00:56:00   | 1 |

### Root Cause Analysis
* Anomaly contribution score for each predicted anomaly point. (pd.DataFrame)

**Note!** `TimeStamp` is a required column name, but you can replace the rest column names with your own.

| TimeStamp | Feature_1 | Feature_2 |
|:--------|:-------:|-------:|
| 2023-03-29 00:56:00   | 34 | 64|
| 2023-03-29 00:56:00   | 12 |  88|


### Aggregate Evaluation
* Micro/Macro scores. A list of dictionaries of independent evaluation results from the same model.

  * result1 = {'TP': 1, 'FP': 1, 'FN': 0,  'precision': 0.5, 'recall': 1.0, 'F1': 0.667}

  * result2 = {'TP': 1, 'FP': 1, 'FN': 1,  'precision': 0.5, 'recall': 0.5, 'F1': 0.5}


## Data Pre-Processing 
The start and end of an anomaly is often unclear, and when manually labelled, the labels might not
be very reliable. As a remedy, you have the option to expand the start and end of an anomaly to tolerate ambiguous points.
Two configurations associated with it are:


* Adjust_true_label (Bool): If your true label is not reliable, set this parameter to be `True` to tolerate ambiguous points.
* Ambiguous_tolerance (Int): If `Adjust_true_label` is set to `True`, then set the number of ambiguous points to be tolerated.



# Use the API
We have an example notebook to help you get started




