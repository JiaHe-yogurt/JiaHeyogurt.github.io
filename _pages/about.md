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

Installation & Import
======
Anomaly-Detection-Model-Evaluation is supported across Windows, Mac and Linux on Python 3.0+.


<pre>
pip install Package-name
from Package-name import functions
</pre>

Getting started
======
Anomaly-Detection-Model-Evaluation targets at evalutating models performance only, it requires true label and output from any model. You should use their own tool for model training. To use the metrics, you need to set some metric configurations, which will be introducted in the following section. 


Data Schema
------
Each evaluation metric may require different input. We examplify the input format for each metric here, and introduce metrics in detail in separate pages.

* Point-wise/Segment-wise unadjusted/adjusted score
  * True label

| TimeStamp | label | rootcause |
|:--------|:-------:|--------:|
| 2023-03-29 00:56:00   | 0 | NaN   |
| 2023-03-29 00:56:00   | 1 | Cpu pressure   |

  * Predicted label

| TimeStamp | label | 
|:--------|:-------:|
| 2023-03-29 00:56:00   | 0 | 
| 2023-03-29 00:56:00   | 1 |


Parameters
------


* Adjust_true_label
  * Ambiguous_tolerance
* Adjust predicted label
  * Alert delay tolerance
  * Alert lagging tolerance


Output
------




