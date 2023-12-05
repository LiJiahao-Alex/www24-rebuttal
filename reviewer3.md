```
We sincerely thank you for carefully reviewing the paper and providing insightful feedback. We are very sorry that some contents have not been clearly conveyed due to our expression. We will clarify and explain in the following.
```

# 1. OCC v.s. SOD
We are sorry that the statement in Section 2 (lines 243-254) may have cause readers the misunderstanding that OCC is completely different from SOD. In fact, we didn't say in the paper that they're completely different. On the contrary, we show in Section III (312-318 lines) that the OCC is a degenerate case of SOD problem. With the help of the formal definitions in Section III, we illustrate below the differences and connections between OCC and SOD.

- **Difference.** $Y_{X_{OCC}}=\{(x, y)|\forall x \in X_{OCC}, y=1\}$, while $$Y_{X_{SOD}}=\{(x, y)|\forall x \in X_{SOD}, y=1,2, \cdots, k, 1<k \leq| X_{SOD} \mid\}$$
- **Connection.** When $k=1$, the SOD problem degenerates to the OCC problem.

In simple terms, although SOD and OCC both detect unknown semantics in the open set, OCC explicitly requires the known semantics to be single semantics. This limiation makes OCC methods ineffective when dealing with unlabeled multi-semantic data.

# 2.Overgeneralization problem
We formulate the statement of the overgeneralization problem mathematically in Chapter V (357-382 lines) Eq(2-3). In simple terms, the overgeneralization problem can be understood as that in the unlabeled multi-semantic data environment, the autoencoder loses the ability to learn semantic information. Instead, it learns low-level features and only performs data reconstruction similar to the identity function, unable to capture the high-level semantic information of the data in the latent space.

# 3.Rest-vs-one

## 3.1 Label-free, multi-semantic, exclusiveness, semanticity, compatibility, and rarity.

The definition of RvO is given in Section IV, Eq1. The notation here is the same as in Section III. We illustrate the correspondence of RvO with respect to six characteristics below.

- Label-free. $\forall{(X,\widetilde{X})}\in{RvO(\mathcal{X})}, Y_X=\emptyset$ when training.
- Multi-semantic. $\because{\widetilde{k}-k=1,\widetilde{k}=K}, \therefore{k=K-1>1}$
- Exclusiveness. $\forall{(X,\widetilde{X})}\in{RvO(\mathcal{X})},X\cap{\widetilde{X}}=\emptyset$
- Semanticity.
- Compatibility.
- Rarity.$\forall{(X,\widetilde{X})}\in{RvO(\mathcal{X})},\rho\approx\frac{1}{K}$

## 3.2

Rest-vs-one (RvO) protocol is explained and discussed in Section IV (321-342 lines). The introduction of RvO involves the definition of the SOD problem in Section III, the shortcomings of the OSR evaluation method in Section II, and the six characteristics of the SOD problem in Section I.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxNDMwNjg4MzcsLTgyNjEyODM0MSwtMT
kzOTg5MTYsLTIxMjQxMjQ1NDAsNzEwMTc5Njk0LC0xMjU3MzIy
ODkzLDQ3MjQ3MDMwMywtMTA5ODgwMjAxXX0=
-->