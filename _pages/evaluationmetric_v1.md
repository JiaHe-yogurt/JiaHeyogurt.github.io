---
permalink: /evaluationmetric_v1/
title: "Evaluation Metric V1"
author_profile: true
redirect_from: 
  - /md/
  - /markdown.html
---
The most widely adopted evaluation tools include well-known metrics like precision, recall and F1 used in binary
classification. However, many studies point out the shortcomings of using con-
vention metrics to time series. One of the most significant issues is that
in real life an anomaly usually lasts for a period of time, which we refer to as
an event. Often times we are more interested in if an event has been detected
or not, rather than the number of anomaly points being detected, thus classic
point-wise metric can misrepresent model’s behavior. We support segment-wise evaluation, where each
contiguous segment of anomalous points is considered one event.

Besides, a predicted event being off by a few time steps might still be very useful and can be count as 
an effective prediction. On the other hand, if the alert is too late to prevent damage, then the alert is 
useless. Furthermore, FPs that are continuation of TP  can also be tolerated if the lagging is within tolerance.
We provide configurations to adjust predicted label based on these considerations.

Overall, we provide both point-wise and segment-wise metric so you can choose the appropriate metric based on anoamly type. 
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

## Point-Wise



### Unadjusted
This is the most commonly used approach for [binary classification](https://en.wikipedia.org/wiki/Precision_and_recall_). We examplify the approach below.


<table>
  <tr>
   <td>True label</td> <td>0</td> <td>0</td> <td>0</td>  <td>1</td> <td>1</td> <td>1</td>  <td>1</td> <td>1</td> <td>0</td> <td>0</td> <td>0</td> <td>1</td> <td>1</td> <td>1</td> <td>1</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td>
   </tr>
  <tr>
   <td>Predicted label</td> <td>0</td> <td>0</td> <td>0</td>  <td>0</td> <td>1</td> <td>1</td>  <td>1</td> <td>1</td> <td>1</td> <td>1</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>1</td> <td>0</td> <td>0</td> <td>1</td> <td>1</td>  
  </tr>
  <tr>
    <td colspan="1">Count</td> <td colspan="3">3TN</td> <td colspan="1">1FN</td>  <td colspan="4">4TP</td> <td colspan="2">2FP</td> <td colspan="1">1TN</td> <td colspan="3">3FN</td> <td colspan="1">1TP</td> <td colspan="2">2TN</td> <td colspan="2">2FP</td> 
  </tr>
</table>

### Adjusted
First adjust predicted label before computing scores if you want to tolerate detection delay and  laggings. If accepted detection delay and lagging are both 3 timestamps, then we get the following counts 

<table>
  <tr>
   <td>True label</td> <td>0</td> <td>0</td> <td>0</td>  <td>1</td> <td>1</td> <td>1</td>  <td>1</td> <td>1</td> <td>0</td> <td>0</td> <td>0</td> <td>1</td> <td>1</td> <td>1</td> <td>1</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td>
   </tr>
    <tr>
   <td>Predicted label</td> <td>0</td> <td>0</td> <td>0</td>  <td>0</td> <td>1</td> <td>1</td>  <td>1</td> <td>1</td> <td>1</td> <td>1</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>1</td> <td>0</td> <td>0</td> <td>1</td> <td>1</td>  
  </tr>
  <tr>
   <td>Adjust predicted label</td> <td>0</td> <td>0</td> <td>0</td>  <td>1</td> <td>1</td> <td>1</td>  <td>1</td> <td>1</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>1</td> <td>1</td>  
  </tr>
  <tr>
    <td colspan="1">Count</td> <td colspan="3">3TN</td> <td colspan="5">5TP</td>  <td colspan="3">3TN</td> <td colspan="4">4FN</td> <td colspan="2">2TN</td> <td colspan="2">2FP</td> 
  </tr>
</table>

## Segment-Wise
### Unadjusted
Use raw prediction without any prediction adjustment.

Segment-Wise involved treating each contiguous segment of anomalous as one event.

 <table>
  <tr>
   <td>True label</td> <td>0</td> <td>0</td> <td>0</td>  <td>1</td> <td>1</td> <td>1</td>  <td>1</td> <td>1</td> <td>0</td> <td>0</td> <td>0</td> <td>1</td> <td>1</td> <td>1</td> <td>1</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td>
   </tr>
  <tr>
   <td>Predicted label</td> <td>0</td> <td>0</td> <td>0</td>  <td>0</td> <td>1</td> <td>1</td>  <td>1</td> <td>1</td> <td>1</td> <td>1</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>1</td> <td>0</td> <td>0</td> <td>1</td> <td>1</td>  
  </tr>
  <tr>
    <td colspan="1">Count</td> <td colspan="3">1TN</td> <td colspan="5">1TP</td>  <td colspan="2">1FP</td>   <td colspan="1">1TN</td>  <td colspan="4">1TP</td> <td colspan="2">1TN</td> <td colspan="2">1FP</td>
  </tr>
</table>


### Adjusted
First adjust predicted label before computing scores if you want to tolerate detection delay and  laggings.

First adjust predicted label before computing scores if you want to tolerate detection delay and  laggings. If accepted detection delay and lagging are both 3 timestamps, then we get the following counts 

<table>
  <tr>
   <td>True label</td> <td>0</td> <td>0</td> <td>0</td>  <td>1</td> <td>1</td> <td>1</td>  <td>1</td> <td>1</td> <td>0</td> <td>0</td> <td>0</td> <td>1</td> <td>1</td> <td>1</td> <td>1</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td>
   </tr>
    <tr>
   <td>Predicted label</td> <td>0</td> <td>0</td> <td>0</td>  <td>0</td> <td>1</td> <td>1</td>  <td>1</td> <td>1</td> <td>1</td> <td>1</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>1</td> <td>0</td> <td>0</td> <td>1</td> <td>1</td>  
  </tr>
  <tr>
   <td>Adjust predicted label</td> <td>0</td> <td>0</td> <td>0</td>  <td>1</td> <td>1</td> <td>1</td>  <td>1</td> <td>1</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>0</td> <td>1</td> <td>1</td>  
  </tr>
  <tr>
    <td colspan="1">Count</td> <td colspan="3">1TN</td> <td colspan="5">1TP</td>  <td colspan="3">1TN</td>   <td colspan="4">1FN</td>  <td colspan="2">1TP</td> <td colspan="2">1FP</td> 
  </tr>
</table>


