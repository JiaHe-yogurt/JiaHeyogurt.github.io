# Anomaly Detection Model Evaluation
A python module for Time Series Anomaly Detection Evaluation. It includes a suite of evaluation metrics that
supports both common and time-series specific metrics applicable to any Time Series Anomaly Detection Algorithm evaluation.

# Evaluation Metrics
## Precision, recall & F1-score
We support both point-based and segmentent-based evaluation, and you can choose to adjust the prediction or not based on application. Specifically, we provide Point-wise unadjusted/adjusted, segmentent-wise unadjusted/adjusted. Point-wise unadjusted (PW) 
and segment-wise unadjusted (SW) are from literature [1], [2]. Point-wise adjusted (PWA) and segmentment-wise adjusted (SWA) are variations of [3] and [4], respectively.

_[1] PW: https://en.wikipedia.org/wiki/Precision_and_recall_

_[2] SW: [Detecting spacecraft anomalies using lstms and nonparametric dynamic thresholding](https://dl.acm.org/doi/pdf/10.1145/3219819.3219845?casa_token=cJTVySbTmakAAAAA:-c4BMSlox-OilLLJQBJ2FmVRFGEXWo8fW5GQzpgO8WApcxt8K2ksdyi5kcrgMrRZTFS-PlS0x9ZA)_

_[3] [Time-Series Anomaly Detection Service at Microsoft](https://dl.acm.org/doi/pdf/10.1145/3292500.3330680?casa_token=fQajYOongWYAAAAA:Fu3-x3SJDSd3Nbh6nsUJJCJR2AsAsa1vQZYEH-zdkBNOb3h6L7bpmIMHC68aJClaff92eOk2DirN)_

_[4] [Unsupervised Anomaly Detection via Variational Auto-Encoder
for Seasonal KPIs in Web Applications](https://dl.acm.org/doi/pdf/10.1145/3178876.3185996 )_

## Root Cause Analysis
Some multivariate anoamly detection models compute anomaly contribution score for each feature, which represent the possibility of being the real root cause. We use HitRate@P% to evaluate the performance of anomaly diagnosis. It's used to measure how many ground truths have been included in the top candidates. Refer to  [Multivariate Time-series Anomaly Detection via Graph Attention Network](https://ieeexplore.ieee.org/document/9338317?denied=) for detail.

## Alert Latency
We report latency statistics. For eeach anomaly alert, we compute the alert latency, which is the diference in timestamp between true labels and predicted labels. We visualize latency distribution compute percentiles.

## Micro and Macro Scores
We support micro and macro evaluation. This can be used when users evaluate the same model on multiple datasets, and want to have a aggregated evaluation. 




# Example

example.py shows how to use all the metrics.

# Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

#  Trademark
Trademarks This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft trademarks or logos is subject to and must follow [Microsoft’s Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks). Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship. Any use of third-party trademarks or logos are subject to those third-party’s policies.

