Speculative Lock Elision: Enabling Highly Concurrent Multithreaded Execution

This paper introduces a methodology to speculative elide false positive lock dynamically and showed how to implement such a method on existing architectures. There are two phenomenons in false shared locks. First, most executions do not perform store operations. Second, different threads update different positions. Manually optimizing the two circumstances will extend software development time. Ideally, hardware could resolve the problem automatically. The method proposed in this paper does not depend on semantic lock/release patterns. Instead, it performs detection directly on instructions. 

There are two assumptions the authors have made: 1. Data read within a speculatively executing critical section is not modified by another thread before the speculative critical section completes. 2. Data written within a speculatively executing critical section is not accessed (read or written) by another thread before the speculative critical section completes. 

Essentially, the method first executes the critical section as if without violation and then rollback through existing buffer and cache coherence protocols once detects collisions.

It seems that the simple method can be easily adapted to existing architectures.

The experimental results are pretty good. For most of the benchmarks, SLE shows consistent performance improvement using different cache protocols.

Experiments are performed on a simulator, which was the right thing to do but just not persuasive enough.

If a program heavily uses nested locks, then the method cannot gain much performance benefits. 

If a program has a large critical section and fails frequently, the method may suffer from performance degradation. And in fact, because the method executes the critical section once before acquiring, we can envision more situations where inefficiencies are revealed. So probably more real-world workloads can be evaluated. 

I think the difference between HTM and SLE is that HTM reties forever without requiring locks. 
