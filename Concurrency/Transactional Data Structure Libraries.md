Transactional Data Structure Libraries

Traditional concurrent data structure designs focus on singleton operations which only has a single effect on data structures. Unfortunately, composing multiple singleton operations do not render a valid transaction. The only way to enable transactions is by using locks and transactional memory, which have significant overhead comparing with lock-free data structures. This paper proposes a method to build transactional operations based upon non-transactional concurrent data structures without sacrificing performance.

This paper proposes a transactional data structure library (TDSL) in which transactional operations employ concurrent data structure for accelerating.

TDSL is composable. Different operations for a concurrent data structure could be bundled together and form a transaction. More than that, operations belong to different data structures can be put together in a transaction.

TDSL includes a set of optimization strategies to explore disjoint parallelism and reduce transaction overhead, including read-set reduction, non-transactional index, and fast-abort.

I found the non-transactional index is quite confusing. It is operated outside of the whole transaction, leading to a series of tricky fixes.

Besides, I would like to blame that the figures in this paper are not well drawn. Many of them are low-resolution pictures. Colors, shapes, and composing were apparently not considered.

