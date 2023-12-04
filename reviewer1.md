# 3.Choice of evaluation metrics
Thank you very much for your constructive suggestions, which made us realize that adding some context would better explain the reasons for the selection of evaluation metrics. Limited by the number of pages in the article, we explain in (349-352 lines) why AUROC is not sufficient for comprehensive evaluation and give the other two evaluation criteria AUPRC and F1 score. We cited reference [24] to help us explain the specific reason, and your comments made us realize that this reduces the smoothness of reading experience. We make the following augmented description of the choice of evaluation.

## 3.1 Why is AUROC not enough to evaluate?
**AUROC ignores data imbalance.** The AUROC is calculated using the area under the ROC curve, which is plotted from the True Positive Rate (TPR) and False Positive Rate (FPR) at different thresholds. 
$$TPR = \frac{TP}{TP+FN}$$
$$FPR = \frac{FP}{FP+TN}$$
The whole focus of TPR and FPR is **the prediction ability of positive samples**, that is, the correct TPR of positive samples is predicted and the confusion of positive samples caused by the wrong prediction of negative samples. When the sample is **imbalanced**, FPR will be a bad indicator because **the amount of TN is large, the effect of FP becomes small, and FPR changes very little**.

## 3.2 Why AUPRC?
For above situation, precision will be a better indicator, the impact of FP will be highlighted, and TP is much smaller than TN.
$$precision = TP/(TP+FP) = 1 - FP/(TP+FP)$$
For the case of imbalanced data distribution, TP<<TN, precision can more highlight the impact of FP. Therefore an additional evaluation AUPRC, which is the area under the precision-recall curve, is added.

## 3.3 Why F1-Score?
Both AUROC and AUPRC are the results of different emphasis on concerns. F1-score is a metric that takes into account both precision and recall, that is, the harmonic mean of precision and recall. 

$$F1=2*\frac{precision*recall }{precision + recall}$$

F1 is equivalent to the comprehensive evaluation metric of precision and recall.
```
[24] Faezeh Movahedi, Rema Padman, and James F. Antaki. 2023. Limitations of receiver operating characteristic curve on imbalanced data: Assist device mortality risk scores. The Journal of Thoracic and Cardiovascular Surgery 165, 4 (2023), 1433–1442.e2. https://doi.org/10.1016/j.jtcvs.2021.07.041
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUwMDAyMDIxOCw0NjAxMTE5Niw1NDQxMz
Q5OTksLTIwNTkzNDg0NjAsMTQwNzQxNTc2NCwxMjUyNjY5NTYx
LC0yMTQ2MTk2MzgwXX0=
-->