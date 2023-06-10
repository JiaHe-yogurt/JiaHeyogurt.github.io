---
permalink: /rootcauseanalysis/
title: "Root Cause Analysis"
author_profile: true
redirect_from: 
  - /md/
  - /markdown.html
---

In the case of multivariate time-series, some methods [for example MTAD-GAT model](https://ieeexplore.ieee.org/document/9338317?denied=) also provide useful insights for anomaly diagnosis. In
real applications, those insights help people find the root cause of an incident and save the efforts to resolve it. We provide HitRate@P to evaluate model's performance of root cause analysis. To use this 
metric, you need to know the true root cause.

## HitRate@P
HitRate is used to measure how many ground truths have been included in the top P candidate features with largest anomaly contribution score. Let GT be the ground truth root cause, TC@P be the top root cause contributors recognized from the model, then:
$$HitRate@P = \frac {\textbf{Overlap} (GT, TC@P)} {|GT|}$$
P is configurable and should be no greater than the number of features.



## Data Schema
* To use the metric, we require you provide anomaly contribution score for each predicted anomaly point in pd.DataFrame.

**Note!** `TimeStamp` is a required column name, but you can replace the rest column names with your own.

| TimeStamp | Feature_1 | Feature_2 |
|:--------|:-------:|-------:|
| 2023-03-29 00:56:00   | 34 | 64|
| 2023-03-29 00:56:00   | 12 |  88|


