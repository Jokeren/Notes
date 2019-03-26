This paper introduces two important utilities that following the busy-wait methodology---spinlock and barrier. By reviewing the pros and cons of previous implementations, the paper proposes efficient implementations of spinlock and barrier. In the experiments running on the BBN Butterfly, the new spinlock and the new barrier outperformed the previous techniques and were scalable up to 80 processors.

It first presents a scalable spin lock design （MCS lock) that guarantees FIFO order among processors that request for locks, spins only on local variables, requires just a constant amount of memory per lock.

It also presents a barrier that only generates O(1) remote reference per processor and can be accelerated by just accessing local flag variables.

1. Busy wait algorithm generally may bring traffics on wires, which requires the delicately designed algorithms to overcome. 

2. Back in that time, some processors do not support CAS atomic operation, which is famous today. On these processors, MCS lock selects another path using fetch-and-store to simulate the CAS behavior, resulting in unfairness.

I have questions regarding the pseudo code, where atomic variables are not marked. Based on my understanding, at least most of the operations in MCS lock require atomic access to prevent reordering. Is it possible that back at that time, compiler reordering is not popular in commercial compilers?
