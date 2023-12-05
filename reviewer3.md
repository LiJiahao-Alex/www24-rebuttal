```
We sincerely thank you for carefully reviewing the paper and providing insightful feedback. We are very sorry that some contents have not been clearly conveyed due to our expression. We will clarify and explain in the following.
```

# 1. OCC v.s. SOD
We are sorry that the statement in Section 2 (lines 243-254) may have cause readers the misunderstanding that OCC is completely different from SOD. In fact, we didn't say in the paper that they're completely different. On the contrary, we show in Section III (312-318 lines) that the OCC is a degenerate case of SOD problem. With the help of the formal definitions in Section III, we illustrate below the differences and connections between OCC and SOD.

- **Difference.** $Y_{X_{OCC}}=\{(x, y)|\forall x \in X_{OCC}, y=1\}$, while $$Y_{X_{SOD}}=\{(x, y)|\forall x \in X_{SOD}, y=1,2, \cdots, k, 1<k \leq| X_{SOD} \mid\}$$
- **Connection.** When $k=1$, the SOD problem degenerates to the OCC problem.

In simple terms, although SOD and OCC both detect unknown semantics in the open set, OCC explicitly requires the known semantics to be single semantics. This limiation makes OCC methods ineffective when dealing with unlabeled multi-semantic data.

# 2.Overgeneralization problem
The statement of the overgeneralization problem, in addition to being well-documented in previous references[A,B,C,D], we also formalize it in Chapter V (lines 357-382).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMjQxMjQ1NDAsNzEwMTc5Njk0LC0xMj
U3MzIyODkzLDQ3MjQ3MDMwMywtMTA5ODgwMjAxXX0=
-->