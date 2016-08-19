#A programming system for future proofing performance critical libraries

##Source

PPoPP '16 Proceedings of the 21st ACM SIGPLAN Symposium on Principles and Practice of Parallel Programming

http://dl.acm.org/citation.cfm?id=2851178&CFID=827624417&CFTOKEN=33754078

##Problem

Performance portability has been a critical issue in heterogeneous systems. However, portability requires archecture-netural implementaions, while high-performance compells programmers focus in specific archectures. Existing technqiues, such as overexpressing and nested parallelism, auto data placement, and auto-tuning are presented to solve the contradiction.

##Motivation

Tangram is a high-level language, more general than DSL, that combines above technqiues together to provide high-performance and portability across disparate archectures. 

##Solution

**Codelet**

Multiple independent codelets form different kernels. The compiler composes a series of codelets, referred to as specturm, to produce multiple ASTs. After pruning the AST set, the compiler make optimization on each AST from the set. Then in runtime, both input adaptation and micro-profiling are appiled to select best kernels.

**Containers**

The container facilitates easy reasoning about transformation, like tiling, vectorization, privation, and blocking.

**Maintainability**

We could use Tangram primitives to extend existing programs.

##My Questions&Notes

1. Could Tangram achieves substantial performance on multi-gpu system?