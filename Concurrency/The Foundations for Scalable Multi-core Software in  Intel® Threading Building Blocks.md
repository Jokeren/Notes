# The Foundations for Scalable Multi-core Software in  Intel® Threading Building Blocks 

## Source

https://www.semanticscholar.org/paper/The-Foundations-for-Scalable-Multicore-Software-in-Kukanov-Voss/7b55610961c63b86141f37c68e73e0326fae0693

## Problem

To provide efficient performance and software portability on multi-core machines, we need a light-weight parallelism library.

## Motivation

The task scheduler is inspired by the cilk scheduler which has work-stealing support.

## Solution

1. Breadth-First theft and depth-First work

Each thread first takes the front of the deepest list of its pool. If there is no ready task, it will steal from the front of the shallowest list of another pool. 

2. Continuation tasks

The "Breadth-First Theft and Depth-First Work" may cause a processor's stack to overflow. So TBB scheduler can force a thread to only steal tasks that are at the deeper level than waiting tasks. It can also use a continuation task to replace a task itself by a continuation task.

3. Scheduler bypass and task recycling

To skip scheduler overhead, it can bypass scheduling phase. We can recyle a task to avoid repeatedly allocation and deallocation.

4. Scalable memory allocation

TBB keeps a thread-private heap for small objects. Heaps are separated by different bins that have different sizes. A bin only points to a single active block. full blocks, empty blocks, and the single active block are chained in a double-linked list. TBB also keeps two free lists.

## My Questions&Notes

1. The semantics of this TBB scheduling are a little trivial, where it needs users to specify the number of reference counts.

2. No comparison with cilk performance.