# The Implementation of the Cilk-5 Multi-threaded Language

## Source

PLDI '98 Proceedings of the ACM SIGPLAN 1998 conference on Programming language design and implementation 
https://dl.acm.org/citation.cfm?id=277725

## Problem

The previous cilk implementations have several problems. The original cilk-1 exposes parallelism "by hand". The following cilk-4 performed stack-based allocation of allocation frames. 

## Motivation

Cilk-5 employs a "work first" strategy to minimize the overhead to work, even at the expense of overheads contribute to the critical path.

## Solution

1. Define critical path overhead and work overhead. Because critical path impact has a more direct influence on the performance, we should try to minimize it first.

2. A fast clone compilation to add little support for parallelism. A slow clone compilation that has full support for parallelism.

3. THE protocal to steal and push tasks into the task dequeue. 

## My Questions&Notes

1. One disadvantage of cilk-5 is that memory allocation happens on heap, which induce memory fragment problems and needs to use pointer to link activation records.

2. It implements the concurrent dequeue with locks, which can be replaced  by lock-free dequeues.

3. Only support one sync semantic, without syncrhonization on variables.