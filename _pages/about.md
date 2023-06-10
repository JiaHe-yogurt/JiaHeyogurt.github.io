---
permalink: /
title: "Anomaly Detection Model Evaluation"
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

Anomaly-Detection-Model-Evaluation targets at evalutating models performance only, it requires true label and prediction from any model. You should use their own tool for model training. To use the metrics, you need to set some metric configurations. 

## Terminology
We define terms that we will use throughout the document. Definitions are partly borrowed from [here](https://learn.microsoft.com/en-us/legal/cognitive-services/anomaly-detector/ad-transparency-note).

| Term | Definition |
|:--------|:-------:|
| True Position (TP)  | The system-detected anomaly correctly corresponds to an actual anomalous event.  |
| True Negative (TN)  | The system correctly doesn't detect any anomaly when metrics data follows a historical pattern that is within the range of normal operations.|
| False positive (FP)  | The system incorrectly detects an anomaly when there's no anomalous event.|
|False negative (FN)  | The system fails to detect an anomaly when an anomalous event has occurred.|
|False negative (FN)  | The system fails to detect an anomaly when an anomalous event has occurred.|
|Precision  |Indicates how many detected anomalies correspond to actual abnormal events. $Precision = \frac {TP}{TP+FP}$. |
|Recall  |Indicates how many actual anomaly events are detected. A recall score of 1.0 means that every actual anomaly event is detected. $Recall = \frac {TP}{TP+FN}$|                
|F1  |Indicates model's balanced ability to both capture anomly events (recall) and be accurate with the cases it does capture (precision). $F1 =  2\frac {Precision* Recal}{Precision+ Recal}$|                





## Data Pre-Processing 
The start and end of an anomaly is often unclear, and when manually labelled, the labels might not
be very reliable. As a remedy, you have the option to expand the start and end of an anomaly to tolerate ambiguous points.
Two configurations associated with it are:


* Adjust_true_label (Bool): If your true label is not reliable, set this parameter to be `True` to tolerate ambiguous points.
* Ambiguous_tolerance (Int): If `Adjust_true_label` is set to `True`, then set the number of ambiguous points to be tolerated.



# Use the API
We have an example notebook to help you get started




