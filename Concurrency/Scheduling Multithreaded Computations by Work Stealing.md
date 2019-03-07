# Scheduling Multithreaded Computations by Work Stealing

## Source

Journal of the ACM (JACM) JACM Homepage archive 
Volume 46 Issue 5, Sept. 1999 

https://dl.acm.org/citation.cfm?id=324234

## Problem

This paper presents a work-stealing scheduler for multi-threaded applications. It shows that the time bound of work-stealing algorithm is T1/P + O(T_infini), which can be proved by a greedy scheduler. The space upper bound is S1P.

## Motivation

The (P, M) recycling game.

## Solution

Comparing with static work-sharing, the migration of threads occurs only when a thread has nothing to do, whiel work-sharing always migrates threads.

The busy leaves property gaurantees that at every time step, an instruction in the spawn-tree must has a processor working on it.

Work stealing has been built into cilk and openmp to provide efficient scheduling.

Although work-stealing is good, it does overlook dynamic thread spawn and thread join costs. Therefore, it seems that for a program with multiple fine-grained regions, traditional schedulers do not render good results. PPoPP'19 has an interesting paper which dynamically controls the threads under the control of an oracle. GPU solve this problem in a brute-force way. It just spawns a lot threads and does not allow users to control spawn activities, unless using dynamic kernel launch. Therefore, to match GPU semantics, CPU parallelism models, such as OpenMP needs to add special controls such as control loop which turns out to reduce performance significantly. How to schedule threads on GPU efficiently? Is there any requirements or needs to do that?

## My Questions&Notes

