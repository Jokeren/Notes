#Barrier Elision for Production Parallel Programs

##Source

PPoPP'15 Proceedings of the 21st ACM SIGPLAN Symposium on Principles and Practice of Parallel Programming

http://dl.acm.org/citation.cfm?id=2688502

##Problem
Large scale scentific applications are consisted of several runtime libraries and implemented by different languages. Further, scientific community is moving toward multi-physics and multi-scale so that the next generation of applications are developed by DSL. In such a situation, programmers often choose conservative synchronization patterns that lead to suboptimal performance. 

##Motivation

We could detect redundant barriers by observing its context. A barrier may be *redundant* if there are no data dependence edges originating from before the barrier on one task and terminating after the barrier on another task.

##Solution

**Elision Rules**

The ideal elision rules inspect the access summary both before and after the barrier. The practical elision rule only elides local accesses preceding any barrier.

**Online Barrier Elision**

It runs a set-up training period and then executes the speculation phase, in which miss speculation might occur. We add a CB status to see whether all processes encounter a miss speculation. If not, we abort the program and restart from the checkpoint in the next time.

**Offline Barrier Elision**

The offline elision method separates training from learning. It begins by learning some samples and extracts shortest-common-suffixes from them. After testing the elision patterns, it uses the derived rule to elide the real production.


##My Questions&Notes

1. How to apply a similar method in my deep learning system.