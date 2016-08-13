#A Wait-free Queue as Fast as Fetch-and-Add

##Source

PPoPP'16 Proceedings of the 21st ACM SIGPLAN Symposium on Principles and Practice of Parallel Programming

http://dl.acm.org/citation.cfm?id=2851168

##Problem
The fast-path-slow-path methodology, that transform lock-free data structures to wait-free, is only available for a series of CASes. However, under heavy contention, most CASes will fails, and we dub this *the CAS retry problem*.

##Motivation

Concurrent structures that use FAA instead of CAS are more practical.

##Solution

**Fast-Path-Slow-Path**
We first attempts several iterations of "fast-path". If necessary, we call a slow-path routine finally, which is guaranteed to success.

**Enqueue**
The "fast-path" enqueue CAS the value of a cell directly. 

The "slow-path" enqueue first publish a state by CAS a cell's *enq* structure. Then, helpers that read the state could help it finish.

**Dequeue**
The "fast-path" first tries to enqueue the pending value. Next, it dequeues the cell by a CAS, changing its dequeue request. 

The "slow-path" dequeue begins by finding a candidate cell that needs to be popped and helps that cell's enqueue request. In the end, it also tries to CAS the cell's dequeue request, returning EMPTY or the value in the cell.


##My Questions&Notes

1. A queue could be enmulated as an infinite array, where we allocate a segment each time, consisting of *N* cells.

2. The value of an enqueued celled will never be changed.

3. How to use a similar methodology for BSTs? Although a general pattern for lock-free structures have been studied, efficient ways of employing other atomic instructions to build wait-free structure have not been revealed yet.