```
Thank you very much for your comment. We are sorry that some of our expressions may not clearly deliver the meaning we intended to convey. We will describe this as clearly as possible in the response below.
```
# 1.Style of writing  
Thank you for your comment. First of all, please allow us to extend our most sincere apology for the writing style that makes your reading experience uncomfortable. At the same time, thank you very much for your modification suggestions in Cons, which provide us with guidelines for writing style transformation to improve readers' reading experience. In terms of writing style, we would like to clarify our motivation for doing so.  
  
- **1.Our original intention is to take into account the reading experience of review experts in various fields.** Specifically, the Semantic Overflow Detection is a complex problem. **It is not easy to grasp the tradeoff between readers who understand terminology clearly and those who prefer abstract analogies. So we used a writing style that abstracts first and formalizes later.** In order to naturally introduce the topic and take into account the readability of reviewers with different specialties, we use a writing style focusing on legibility in the first paragraph (40-83 lines), and use the concept of over-generalization ghost in two places (368, 288 lines). In order to illustrate the abstract analogy at the beginning of the article, we use a large number of formulas and rigorous mathematical expressions. After reading your comments, we deeply realize that this is not clear for readers, and we will simplify the above content according to your suggestion immediately.  
- **2.We have no intention to give up rigor and intelligibility in favor of legibility.** We use concise and rigorous writing style for the vast majority of the paper. **We use a lot of notation and formulas to ensure that our core concepts are rigorously conveyed** as examples in Section III (291-318 lines), Section IV (320-356 lines), Section VI (384-440 lines), Equations (1-12), etc. The concept of overgeneralization ghost appears twice, first in (288 lines) for legibility and abstract understanding, and second in (368 lines) for rigorous mathematical description (Eq. 2-3). The passage between these two concepts is too far apart to make the reader have a unclear reading experience. Your comments have made us deeply aware that some abstract analogies are redundant for readers. We will heed your instruction and remove two abstract analogies immediately.

# 2.Context for concept/example
Once again, please allow us to deeply apologize for uncomfotable reading experience in understanding the concept/example based on the context we provided. Limited by the number of pages in the article, we only provide the main context supplemented by references. We would like to use the (150-160 lines) you proposed as an example to clarify our intention for providing context. 

- "The hypothesized die" and  "surface inspection" are **not concepts but part of examples**, so it is indeed necessary to understand under the manufacturing scenario.  We use "taking defect detection [8] as a counterexample"(151 lines) as the beginning of the sentence to illustrate this point, and before the end of the sentence, all descriptions and vocabulary should be in the context of defect detection or manufacturing scenario.

- The same goes for "low-level image statistics[3]", which is in the sentence headed by "Another counterexample is"(154 lines), so it is also an example not a concept.

- The actual conceptual statement "semantic anomalies[3]" begins after the "Notably" word (lines 58 to 61).  This concept is a term taken from reference [3].

The structure of this section is to introduce two examples followed by a concept. The begining of the sentence declares whether the whole sentence is an example or a concept. If the sentence of example does not end, it still needs to be understood in the context of the current example.

Your suggestions have been very constructive and have given us a reader's perspective on how to improve. Your comment make us deeply realized that our attempt to cite references for context reduction affects the experience of reading. We immediately fixed the problem and expanded all the contexts.
```
[3]Faruk Ahmed and Aaron Courville. 2020. Detecting semantic anomalies. In Proceedings of the AAAI Conference on Artificial Intelligence, Vol. 34. 3154–3162.
[8]Paul Bergmann, Michael Fauser, David Sattlegger, and Carsten Steger. 2019. MVTec AD — A Comprehensive Real-World Dataset for Unsupervised Anomaly Detection. In 2019 IEEE/CVF Conference on Computer Vision and Pattern Recognition (CVPR). 9584–9592. https://doi.org/10.1109/CVPR.2019.00982 
```


# 3.Choice of evaluation metrics
Thank you very much for your constructive suggestions, which made us realize that adding some context would better explain the reasons for the selection of evaluation metrics. Limited by the number of pages in the paper, we explain in (349-352 lines) why AUROC is not sufficient for comprehensive evaluation and give the other two evaluation criteria AUPRC and F1 score. We cited reference [24] to help us explain the specific reason, and your comments made us realize that this reduces the smoothness of reading experience. We make the following augmented description of the choice of evaluation.

## 3.1 Why is AUROC not enough to evaluate?
**AUROC ignores data imbalance.** The AUROC is calculated using the area under the ROC curve, which is plotted from the True Positive Rate (TPR) and False Positive Rate (FPR) at different thresholds. 
$$TPR = \frac{TP}{TP+FN}$$
$$FPR = \frac{FP}{FP+TN}$$
The whole focus of TPR and FPR is **the prediction ability of positive samples**, that is, the correct TPR of positive samples is predicted and the confusion of positive samples caused by the wrong prediction of negative samples. When the sample is **imbalanced**, FPR will be a bad indicator because **the amount of TN is large, the effect of FP becomes small, and FPR changes very little**.

## 3.2 Why AUPRC?
For above situation, precision will be a better indicator, **the impact of FP will be highlighted**, and TP is much smaller than TN.
$$precision = \frac{TP}{TP+FP} $$
$$recall = \frac{TP}{TP+FN} $$
For the case of imbalanced data distribution, TP<<TN, precision can more highlight the impact of FP.  A companion to precision is recall, which measures how many of the positive examples in the sample are predicted correctly (find all) the fraction of all positive examples that are correctly predicted. Therefore an additional evaluation AUPRC, which is the area under the precision-recall curve, is added.

## 3.3 Why F1-Score?

Precision and recall are a pair of contradictory measures. Recall tends to be low when precision is high, while precision tends to be low when recall is high. F1-score is a metric that takes into account both precision and recall, that is, the harmonic mean of precision and recall. 

$$F1=2*\frac{precision*recall }{precision + recall}$$

F1 is equivalent to the comprehensive evaluation metric of precision and recall. Therefore, the best F1 score can more comprehensively evaluate the performance level of the model in the best case.

We are very sorry for not introduce the above content in order to accommodate the page limit of the paper. We immediately supplemented the paper according to your suggestions and guidance.
```
[24] Faezeh Movahedi, Rema Padman, and James F. Antaki. 2023. Limitations of receiver operating characteristic curve on imbalanced data: Assist device mortality risk scores. The Journal of Thoracic and Cardiovascular Surgery 165, 4 (2023), 1433–1442.e2. https://doi.org/10.1016/j.jtcvs.2021.07.041
```
# 4.Relevance to Web audience

## 4.1 An area in Semantic Web and Knowledge Management(SW&KM)
As reviewer TEpt said, the semantic overflow detection, the content of our paper, is a hot area of the semantic web and knowledge management[A,B,C,D,E,F], which is relevant to the Semantics and Knowledge track of the Web Conference 2024.
>The article is framed in the field of track study. Semantic overflow detection is an area of interest in semantic web and knowledge management. ---Reviewer  TEpt

To the best of our knowledge, the earliest systematic exposition on SW&KM comes from a paper[D] published in WWW 2002.
```
[A]Davies J, Fensel D, Van Harmelen F. Towards the semantic web. Ontology-Driven Knowledge Management. 2003.
[B]Antezana E, Kuiper M, Mironov V. Biological knowledge management: the emerging role of the Semantic Web technologies. Briefings in bioinformatics. 2009 Jul 1;10(4):392-407.
[C]Svetel I, Pejanović M. The role of the semantic web for knowledge management in the construction industry. Informatica. 2010;34(3).
[D]Stojanovic N, Handschuh S. A framework for knowledge management on the semantic web. In The 11th International WWW Conference 2002 (pp. 2-4).
[E]Davies J, Lytras M, Sheth AP. Guest editors' introduction: semantic-web-based knowledge management. IEEE Internet Computing. 2007 Sep 24;11(5):14-6.
[F]Chen L, Shadbolt NR, Goble CA. A semantic web-based approach to knowledge management for grid applications. IEEE Transactions on Knowledge and data Engineering. 2006 Dec 26;19(2):283-96.
```

## 4.2 SW&KM follows the in-framework specifications of Web
The Semantic Web and Knowledge Management are framed within the scope of the Web Conference. Machine learning are introduced here **as a tool rather than a topic**. There is no way to give up machine learning tools completely, because of their significance to the Web and the fact that adopting machine learning tools is a trend in recent years[G,H,I]. Some cutting-edge work shows the potential application of machine learning as a tool on the Web, such as Knowledge-based Semantic Communication[J], 

```
[G]Proceedings of the ACM Web Conference 2023. Association for Computing Machinery, New York, NY, USA.
[H]Proceedings of the ACM Web Conference 2022. Association for Computing Machinery, New York, NY, USA.
[I]Proceedings of the ACM Web Conference 2021. Association for Computing Machinery, New York, NY, USA.
[J]
```


# 5.The answer to quesion
As Reviewer TEpt said, ``"semantic overflow detection is an area of interest in semantic web and knowledge management."``SW&KM is the starting point of our paper. We acknowledge the use of machine learning techniques but only as a tool to serve the topic of the paper. We illustrate the relevance of this paper and the web conference in ``4.Relevance to Web audience``.

```
Once again please allow us to thank you for your comment. We cherish every suggestion to make the paper better, and we will spare no effort to perfect it according to your requirements. Hope our reply dispels your concerns, if you still have concerns please don't hesitate to let us know.
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc2MTQxMjI2NiwzODIyMDgzNTQsLTExOD
AzMzAyMzQsMTMwOTQ2NTExOV19
-->