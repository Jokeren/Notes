Nonblocking Concurrent Data Structures with Condition Synchronization

This paper focuses on uncharted territory in concurrent data structure theory. Previously linearization points and progress conditions only define operations that are complete but ignore operations that may spin and wait. This paper proposes a complete theory by extending linearization history to augmented linearization history. It defines request and follow-up linearization points for these partial concurrent operations and demonstrates the usage by designing two concurrent dual data structures that store both data and requests.

This paper is meaningful from both practical and theoretical aspects. In the real world, many applications need operations that wait until some conditions meet. Therefore, there's a need to implement partial concurrent operations and define rules to evaluate the correctness of these operations.

To show the effectiveness of partial concurrent data structures, the author design lock-free dual-queue and lock-free dual-stack, based on prior standard totalized concurrent data structures. Experiments show that these dual structures scale on UltraSPARC III processors and are significantly faster than lock-based data structures.

There remains a question of designing dual data structures for tree-based concurrent data structures since it is hard to know if operations underneath are request or data.

In addition, adding a request field to fundamental data structures increases memory footprint significantly. In principle, we should keep a low memory footprint and simple operations in concurrent circumstances. 





