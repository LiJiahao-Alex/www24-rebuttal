```
Thank you very much for your comment. I am sorry that some of our expressions in the article may have caused misunderstandings. In order to convey what we want to express more clearly, we have made the following reply.
```
# 1. Distinction between OSR and SOD
Thanks for your comments. First of all, please allow us to apologize for some misunderstandings caused by the design of our pictures. We will first clarify the misunderstanding below, and then explain the distinction between OSR and SOD.

## 1.1 The question mark tag represents no label
When a question mark appears on the blue tag, it means that there is no label information for this data.

## 1.2 Difference between OSR and SOD
- OSR is **supervised** learning, while SOD is **unsupervised** learning. 
- OSR requires **data-label (x,y) pairs** for training, while SOD **only requires data x without labels y** for training. 
- OSR aims at **classifying** the knowns and **detecting** the unknowns, while SOD only aims at the **detection** of unknowns.

## 1.3 What if OSR data tagged with "?"
The OSR data is all marked with question marks tag, which means that all label information is removed from the data. At this time, this case does not belong to the research scope of OSR, because OSR is supervised learning, which requires data-label pairs. At the same time, it does not belong to SOD. For large amounts of unsupervised data, there are multiple tasks such as clustering, sorting, compression, etc. Whether this is SOD in the face of large amounts of unsupervised data depends on the specific task.

## 1.4 Being unlabeled is an assumption that conforms to Web data, and it is not a deliberate ignorance of labels.
OSR is built with the default that all data is labeled, so the task of OSR is to not only classify knowns but also detect unknowns in the test data. SOD is built  with the default that data is unlabeled, so the task of SOD is to detect the unknown. Note that the latter is not just a result of ignoring labels for the following reasons. 

- Firstly, being labelless is an external condition, not something that can be artificially created. And label resources are scarce, so it doesn't make sense to remove them or ignore them.
- Secondly, SOD has practical scenarios and significance and is more in line with Web data. 
- Thirdly, the difficulty of SOD is much higher than OSR because of the lack of label information. In the context of Web, most data are unlabeled, or require very high labeling costs. 

Here are two examples for better illustration.

>**OSR.** For example, a face recognition gate machine that requires face-identity (data-label) pairs at training can be deployed to identify employees (knowns classification) and identify outsiders (unknowns detection). Its performance on classification and rejection tasks is not surprising given the large number of data-label pairs used.

>**SOD.** In web data, a large amount of data is available without labels. For example, in the surveillance web system, the police only care about whether the suspect appears (unknowns detection), and do not care about the identity of each person appearing in all the surveillance records (knowns classification). 

It can be seen that SOD is a more complex scenario in line with unlabeled web data. If it is possible to label everyone in the video surveillance except the suspect (OSR case), the difficulty of finding the suspect will be greatly reduced. However, the cost of labeling is high. **Therefore, the SOD is not ignoring the label, but a situation that is unable to access the label.** The SOD is meaningful, and there are specific application scenarios related to the web and big data behind it.

# 2. VAE v.s Ours

We are sorry that we did not clearly explain the comparison between VAE and our performance thus causing some misunderstandings, which we will clarify below.

- VAE is the **best performance obtained under grid search trials** with hyperparameters such as batch size and learning rate.
- VAE performs **a grid search on each dataset separately** for the best performance.
- To show that our approach is effective, we **neither** perform a grid search over hyperparameters **nor** train with separate hyperparameters for each dataset as stated in Section7.1 of paper.
- We evaluate all datasets using **no-tuning policy** to illustrate that our method can perform well even with naive setting.
 - Even when the variance is considered, our method **outperforms VAE in the worst case**.
- In MNIST and Kuzushiji datasets, our method presents superiority. On the Fashion dataset, our method and VAE produce seemingly similar results. In the VAE results, hyperparameter grid search with batch size, beta value, learning rate, patience value of early stopping mechanism, weight decay is used. To explore the potential of performance of our approach, we also use the same technique and report our results in Table 1, denoted by Ours+. 

|      | AUROC| AUPRC | best F1-Score|
|------|------------|-------------|-------------|
| VAE  | 70.61±0.24 | 22.90±0.32  |  31.97±0.25 |
| Ours | 71.22±0.46 |  24.21±0.37 | 33.36±0.40  |
| Ours+ | 74.61±0.39 |  26.84±0.33 | 35.91±0.39  |
Tabel 1-Ours perfomance on Fashion without no-tuning policy

Due to the limitation of the rebuttal time window, we did not use as many alternative hyperparameters as VAE and used Bayesian search instead of grid search to speed up the experiment. Even in this case, we get a good result that shows that our method outperforms the VAE, even when considering the variance.

# 3. Data format
I understand your concern about the field of semantic web and knowledge management, and I would like to explain our research design in the following ways:

Firstly, the choice of MNIST, FashionMNIST, and Kuzushiji datasets was not solely driven by an interest in image processing per se. Instead, these datasets were selected as a medium for exploring the integration of visual and semantic information to enhance the understanding of relationships between entities within the semantic web and knowledge management environment. Recognizing the unique position of image data in modern information sharing and transmission on the web, our study aims to provide new perspectives, emphasizing the irreplaceability of image data in the semantic web and knowledge management. We believe that such research can provide a new approach to the management of knowledge and the representation of semantic information.

Secondly, our research extends beyond the realm of image data processing. In the long run, we are committed to exploring the possibilities of integrating multi-source information within the semantic web environment. The proposed approch to facilitate the possible fusion of image data with traditional forms of knowledge, creating a more comprehensive semantic representation. In doing so, we seek to enrich the content of knowledge graphs and enhance the adaptability of knowledge management systems to multi-modal information.

Additionally, We appreciate your valuable commet, which has provided insightful directions for our research. To better address the needs of the semantic web and knowledge management domain, we plan to broaden the scope of datasets in future research, including various forms of data and delving deeper into semantic understanding. We believe this will provide comprehensive and profound support for our study.

Finally, we sincerely thank you for your guidance. We will make further revisions to the paper to align with your suggestions and the expectations of the conference. We look forward to showcasing our unique contributions to the semantic web and knowledge management domain in the final version.


# 4. Appendix analysis
Thank you for your careful review of our paper and your valuable suggestions. We understand your point about the lack of sufficient discussion for the additional analysis of appendix tables in the paper. We realize that the analysis in these appendices is essential for a deeper understanding of the research questions. Additional analysis could provide a more comprehensive interpretation of our findings as well as a close relationship to the main discussion. We discuss the results of these additional analyses in more detail and elaborate on how they interrelate to the main research findings and the implications for the research.

## 4.1 Table-6
Table 6 in the appendix is explained in Section 7.2 of the paper (519-521 lines) and Appendix A (1047-1050 lines). Since the three datasets have different labels, we use the numbers 0-9 as a uniform label in order to simplify the table design. The purpose of Table 6 is to illustrate the correspondence between the numbers 0-9 and the true labels.

## 4.2 Table-7,8,9
Tables 7-9 show the experimental results performed according to Eq.1 in Section 4 of the paper (321-338 lines).  The three tables show the AUROC, AUPRC, and best F1 score evaluation results in turn. Table 2 in the paper is the mean from Table 7-9 as described in Section 7.2 (541-547 lines ) and Appendix B (1052-1105 lines ). Our method outperforms the comparison methods in most of the molecular experiments. SAE achieves a certain performance improvement compared to AE, which means that weighted sparse regularization is helpful for semantic learning. DAE also has a certain improvement compared with AE, which indicates that the noise addition and denoising processing of data can help the learning of semantic information. VAE achieves the second best result overall, which reflects that modeling the latent space is beneficial for learning semantics. MemAE achieves the third best overall performance, which verifies the previous point, but also illustrates that a reasonable latent space model design is required for semantic learning to achieve good results. We'll add bar charts to get a better sense of how all the algorithms compare.

# 5. Why called semantic overflow detection?

The name semantic overflow detection was originally inspired by HTTP 404 Not Found Error. Specifically, when the Web data or page is accessed by an address or URL, a 404 error is returned to let the consumer knwon if the target does not exist. It would be disastrous if the target didn't exist and the Web returned what the system thought was an approximate page or data without telling it. This situation doesn't happen thanks to 404 Not Found Error, however, it does happen in the semantic-level query.

For example, if we deploy a dog classification model on a web page, we want the page to return dog breeds when an instance is queried. However, if the instance is a rare dog (one that does not belong to any of the classification models), a common dog breed will still be returned because the backend of the web page is a preset common dog classification model. How to build a detector between a web page and a model to ensure that access can be denied (just like 404) when queried for semantics not contained in the model is a problem worth studying. 

Based on the above examples, we outline our conception of unknown semantic detection. To illustrate that an unknown semantics is one that is beyond the scope of a predefined semantics, we call it semantic overflow detection, which is to detect the access that is not included by the system preset at the semantic level.



# 6. Definition of semantics

## 6.1 Definition

Semantics in our paper refers to a machine-based description of the meaning implied by data, aiming to make data on the Internet easier to understand and interpret. The semantics in our paper is the desire for web information to be not only human readable, but also machine understandable. Extracting semantic information from data facilitates more advanced information interaction, intelligent search, automated tasks, and knowledge discovery.

## 6.2 Difference between semantics and labels
Semantic and traditional labels are different in the way of formation process, fine granularity and data entity. Here are the details:

- From the perspective of the formation process, semantics are abstracted bottom-up (the result of label-free learning), and labels are defined top-down (the presupposition of label-learning).

- From the perspective of the fine granularity, the fine granularity of labels is pre-defined, and the fine granularity of semantics is determined by the data itself.

- From the perspective of data entities, labels are artificially pre-agreed symbols, and semantics are meaning feature in the data (as Reviewer TEpt said).

In general, semantics focuses more on the semantic meaning of data or feature and helps computers understand the nature of data, while the traditional  labels focus more on the goal of model training and prediction.
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTEwMTIxNDIsMTMyMDU3MTQ3LDExNDI5OD
M5Nyw4MzIwODM5MTEsMTE2MzU4OTIzMywtNDQyMjM5NDQ4LC0x
MzM5NDc2OTM5LDIxNDIxNjAxMzcsLTE4MDAxNTMwOTEsLTk1OT
MwMTY5NCwtMTM5OTM2ODMzNCw0Mzg4NTU3NjksLTExMTY0Njg2
NzgsLTMwMzg5NzQ0NCwxNTE2OTIzNjA5LC02NzUzODY0MDQsMT
A1MTI4MjEwNCwtMTE1OTkzOTA2OCwxOTc2Njg1NDY4LC0zNzQz
MzI1Nl19
-->