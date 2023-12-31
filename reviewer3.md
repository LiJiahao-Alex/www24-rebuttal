```
We sincerely thank you for carefully reviewing the paper and providing insightful feedback. We are very sorry that some contents have not been clearly conveyed due to our expression. We will clarify and explain in the following.
```

# 1. OCC v.s. SOD
We are sorry that the statement in Section 2 (lines 243-254) may have cause readers the misunderstanding that OCC is completely different from SOD. In fact, we didn't say in the paper that they're completely different. On the contrary, we show in Section III (312-318 lines) that the OCC is a degenerate case of SOD problem. With the help of the formal definitions in Section III, we illustrate below the differences and connections between OCC and SOD.

- **Difference.** $Y_{X_{OCC}}=\{(x, y)|\forall x \in X_{OCC}, y=1\}$, while $Y_{X_{SOD}}=\{(x, y)|\forall x \in X_{SOD}, y=1,2, \cdots, k, 1<k \leq| X_{SOD}\mid\}$
- **Connection.** When $k=1$, the SOD problem degenerates to the OCC problem.

In simple terms, although SOD and OCC both detect unknown semantics in the open set, OCC explicitly requires the known semantics to be single semantics. This limiation makes OCC methods ineffective when dealing with unlabeled multi-semantic data.

# 2.Overgeneralization problem
We formulate the statement of the overgeneralization problem mathematically in Chapter V (357-382 lines) Eq(2-3). In simple terms, the overgeneralization problem can be understood as that in the unlabeled multi-semantic data environment, the autoencoder loses the ability to learn semantic information. Instead, it learns low-level features and only performs data reconstruction similar to the identity function, unable to capture the high-level semantic information of the data in the latent space.

# 3.RvO corresponding to six characteristics
The definition of RvO is given in Section IV, Eq1. The notation here is the same as in Section III. We illustrate the correspondence of RvO with respect to six characteristics below.

- **Label-free.** $\forall{(X,\widetilde{X})}\in{RvO(\mathcal{X})}, Y=\emptyset$ where $Y$ represents the set of labels of the data $X$.
- **Multi-semantic.** $\because{\widetilde{k}-k=1,\widetilde{k}=K}, \therefore{k=K-1>1}$
- **Exclusiveness.** $\forall{(X,\widetilde{X})}\in{RvO(\mathcal{X})},X\cap{\widetilde{X}}=\emptyset$
- **Semanticity.** $\forall\left(x_i, y_a\right),\left(x_j, y_b\right) \in$ $Y_X, y_a \neq y_b, x_i \nsim \mathcal{N}\left(\mu_{y_b}, \sigma_{y_b}^2\right), x_j \nsim \mathcal{N}\left(\mu_{y_a}, \sigma_{y_a}^2\right)$
- **Compatibility.**$Y_X\subseteq{Y_{\widetilde{X}}}$
- **Rarity.**$\forall{(X,\widetilde{X})}\in{RvO(\mathcal{X})},\rho\approx\frac{1}{K}=0.1<0.5$ where $\rho$ is the anomaly ratio.

# 4.Evaluation method
Thank you very much for your constructive suggestions, which made us realize that adding some context would better explain the reasons for the selection of evaluation metrics. Limited by the number of pages in the paper, we explain in (349-352 lines) why AUROC is not sufficient for comprehensive evaluation and give the other two evaluation criteria AUPRC and F1 score. We cited reference [24] to help us explain the specific reason, and your comments made us realize that this reduces the smoothness of reading experience. We make the following augmented description of the choice of evaluation.

## 4.1 Why is AUROC not enough to evaluate?
**AUROC ignores data imbalance.** The AUROC is calculated using the area under the ROC curve, which is plotted from the True Positive Rate (TPR) and False Positive Rate (FPR) at different thresholds. 
$$TPR = \frac{TP}{TP+FN}$$
$$FPR = \frac{FP}{FP+TN}$$
The whole focus of TPR and FPR is **the prediction ability of positive samples**, that is, the correct TPR of positive samples is predicted and the confusion of positive samples caused by the wrong prediction of negative samples. When the sample is **imbalanced**, i.e. $\rho<0.5$, FPR will be a bad indicator because **the amount of TN is large, the effect of FP becomes small, and FPR changes very little**.

## 4.2 Why AUPRC?
For above situation, precision will be a better indicator, **the impact of FP will be highlighted**, and TP is much smaller than TN.
$$precision = \frac{TP}{TP+FP} $$
$$recall = \frac{TP}{TP+FN} $$
For the case of imbalanced data distribution, TP<<TN, precision can more highlight the impact of FP.  A companion to precision is recall, which measures how many of the positive examples in the sample are predicted correctly (find all) the fraction of all positive examples that are correctly predicted. Therefore an additional evaluation AUPRC, which is the area under the precision-recall curve, is added.

## 4.3 Why F1-Score?

Precision and recall are a pair of contradictory measures. Recall tends to be low when precision is high, while precision tends to be low when recall is high. F1-score is a metric that takes into account both precision and recall, that is, the harmonic mean of precision and recall. 

$$F1=2*\frac{precision*recall }{precision + recall}$$

F1 is equivalent to the comprehensive evaluation metric of precision and recall. Therefore, the best F1 score can more comprehensively evaluate the performance level of the model in the best case.

We are very sorry for not introduce the above content in order to accommodate the page limit of the paper. We immediately supplemented the paper according to your suggestions and guidance.

# 5. "No test set for anomalies"?
We are very sorry that we may have caused misunderstanding. We have not conveyed the information of "no test set for anomalies". We searched "no test set for anomalies" in the original paper and did not find such a statement either. The only similar quote in paper we find is in Section VI (388 line).
>"there is no test set evaluation feedback during trainining"

We would like to make the following clarification.

- $\forall{(X,\widetilde{X})}\in{RvO(\mathcal{X})}$ The training set $X$ is all known semantics, and the test set $\widetilde{X}$ contains both known semantics and unknown semantics (anomalies).
- For example, the training set is images of handwritten digits with nine semantics from 0 to 8, and the test set is images of handwritten digits with ten semantics from 0 to 9. At this point, the training set does not contain the unknown semantics 9 (anomalies).
- The training set only has data without labels. In the test set, 0-8 are all labeled as known(normal), and 9 is labeled as unknown(anomalies).
- In the training phase, the training set is available and the test set is not.
- In the testing phase, the training set is not available and the testing set is available.
- The three evaluation methods of AUROC, AUPRC and F1 score only can be performed on the test set because the test set has known(0-8) and unknown(9) labels.
- AUROC, AUPRC and F1 score are all evaluated on the test set but not on the training set because the training set has no labels.

In summary, the message we want to convey to the reader is that during training, evaluation cannot be performed. 

# 6.We do not try to "find the best model design" (Q1)
The reading of last paragraph of Section 5 **should be followed up with Section 6 (387-393 lines)**. The logic we like to state is that while finding the best model design is the key to solving the overgeneralization problem, it requires evaluation feedback during trainig. As mentioned in ``5. "No test set for anomalies"?``, evaluation cannot be performed during training, so the "find the best model design" scheme is not feasible. Ideally, the search for the best model design uses performance evaluation as a guide:

``Model A --> Evaluation of A --> Model modification -->
Model B --> Evaluation of B --> Model modification -->
Model C --> Evaluation of C --> Model modification --> ··· ··· ---> the best model design``
 
This is the ideal situation, but during actual training, evaluation cannot be implemented dur to inaccessible of test set. Since the search for the best model design (Plan A) does not work, we turn to an alternative (Plan B). We use Table 1 to clarify the misunderstanding.

|  | Plan A | Plan B |
|--|--|--|
| Method | Find the best model design. | Introduce a generalization suppressor. |
|Limitation| No test set evaluation feedback during training. |/|
|Advantage|/|Do not need test set evaluation feedback during training|
Table 1-Different ways to address overgeneralization problem.

Therefore, we perform the Plan B route and propose the memory module, which does not require continuous evaluation feedback to obtain good performance.

# 7.Model design (Q2)
Model design (Plan A) is a tricky thing, it needs to take into account the characteristics of the dataset. This is exactly why we choose Plan B instead of Plan A.  Plan B is a more general method.

```
Once again please allow us to thank you for your comment. We cherish every suggestion to make the paper better, and we will spare no effort to perfect it according to your requirements. Hope our reply dispels your concerns, if you still have concerns please don't hesitate to let us know. 
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjYwMDE4MjYzLC04ODI1MTEyODEsLTExND
I2MDYxODQsLTM0NTc2Mzk5MSw4ODUwOTAzNjQsLTEyMDQxMjg4
ODYsLTI0NTAzOTgzMCw4MDkyNjM3NzcsLTgyNjEyODM0MSwtMT
kzOTg5MTYsLTIxMjQxMjQ1NDAsNzEwMTc5Njk0LC0xMjU3MzIy
ODkzLDQ3MjQ3MDMwMywtMTA5ODgwMjAxXX0=
-->