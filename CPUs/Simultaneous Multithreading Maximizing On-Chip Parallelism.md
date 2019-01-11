## Source

ISCA'95

https://ieeexplore.ieee.org/document/524578

## Problem

Superscalar processors are limited by instruction dependencies within the single executing thread, and therefore possess both horizontal and vertical waste. Traditional multi-threaded processors solve vertical waste. However, as the these processors issue instruction only from one thread in any cycle, suffer from horizontal waste.

## Motivation

Simultaneous multithreading processors resolve both horizontal and vertical waste.

The objective of simultaneous multithreading is to overcome both long memory latencies and limited available parallelism per thread. Simultaneous multithreading combines the multiple-issue per-instruction features of modern superscalar processors with the latency-hiding ability ofmultithreaded architectures.

## Solution

1. Environment

A simulation method is used to compare the performance among superscalar processors, fine-grain multi-threaded processors, simultaneous multithreading processors, and single-chip multiprocessors. The typical configuration contains 10 functional units of four types, three levels of caches, out-of-order execution. SPEC92 benchmark suite is used to gauge the performance of processors. Only uniprocessor applications are used to avoid synchronization delays and inefficient parallelism.

2. Superscalar vs Fine-grain vs Simultaneous Multithreading

For superscalar processors, functional units are highly underutilized, and there is no dominant source of wasted issue bandwidth and no dominant solution. Therefore multi-threading is a general solution to hide latencies.

Fine-grain multi-threaded processors provide only limited speedup over single-thread execution because of horizontal waste.

Increasing the number of instructions each thread can issue increases processor utilization. However, it also has negative effects such that lower priority threads run at lower speed comparing with higher priority threads. 

3. Cache design

Private I caches eliminate conflicts between different threads in the I cache, while a shared D cache allows a single thread to issue multiple memory instructions to different banks.

4. Simultaneous Multithreading vs Single-Chip Multiprocessing

Single chip multiprocessors statically partition resources. Simultaneous multithreading outperforms single-chip multiprocessing in a variety of configurations, and it requires fewer resources to achieve a given performance level.

## My Questions&Notes

1. "For example, if the next instruction cannot be scheduled in the same cycle as the current instruction, then the remaining issue slots this cycle, as well as all issue slots for idle cycles between the execution of the current instruction and the next (delayed) instruction, are assigned to the cause of the delay."

Why should we assign issue slots for idle cycles as delay reasons?