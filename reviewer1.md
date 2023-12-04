# 3.Choice of evaluation metrics
Thank you very much for your constructive suggestions, which made us realize that adding some context would better explain the reasons for the selection of evaluation metrics. Limited by the number of pages in the article, we explain in lines 349 to 352 why AUROC is not sufficient for comprehensive evaluation and give the other two evaluation criteria AUPRC and F1 score. We cited reference [24] to help us explain the specific reason, but your comments made us realize that this reduces the smoothness of reading.

>The AUROC is calculated using the area under the ROC curve, which is plotted from the True Positive Rate (TPR) and False Positive Rate (FPR) at different thresholds. 
$$TPR = TP/(TP+FN)$$
$$FPR = FP/(FP+TN)$$
When TPR is equal to FPR, that is, the probability that the model predicts a positive sample to be positive is equal to the probability that the model predicts a negative sample to be positive, and the model does not have discriminative power. TPR is equal to FPR, and the corresponding ROC curve is a straight line with y=x, in which case the corresponding AUC is 0.5.
The whole focus of TPR and FPR is the prediction ability of positive samples, that is, the correct TPR of positive samples is predicted and the confusion of positive samples caused by the wrong prediction of negative samples.
When the sample is **highly imbalanced**, FPR will be a bad indicator because **the amount of TN is large, the effect of FP becomes small, and FPR changes very little**.
At this point, precision will be a better indicator, the impact of FP will be highlighted, and TP is much smaller than TN.
$$precision = TP/(TP+FP) = 1 - FP/(TP+FP)$$
For the case of imbalanced data distribution, TP<<TN, precision can more highlight the impact of FP.
```
[24] Faezeh Movahedi, Rema Padman, and James F. Antaki. 2023. Limitations of receiver operating characteristic curve on imbalanced data: Assist device mortality risk scores. The Journal of Thoracic and Cardiovascular Surgery 165, 4 (2023), 1433–1442.e2. https://doi.org/10.1016/j.jtcvs.2021.07.041
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTkxODIxOTg0MiwxNDA3NDE1NzY0LDEyNT
I2Njk1NjEsLTIxNDYxOTYzODBdfQ==
-->