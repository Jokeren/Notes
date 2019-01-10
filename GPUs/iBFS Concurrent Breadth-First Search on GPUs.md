# iBFS: Concurrent Breadth-First Search on GPUs

## Source

Proceeding SIGMOD '16 Proceedings of the 2016 International Conference on Management of Data Pages 403-416.

http://dl.acm.org/citation.cfm?id=2882959

## Problem

GPU performance suffers to running multiple BFS instance. But we could leverage frontier sharing properties and bit operations to optimize iBFS algorithms.

## Motivation

1. Multiple BFS instances might share same frontiers so that we only need to load them from global memory once. 

2. The speedup of iBFS is determined by the sharing ratio of frontiers. Hence, we should propose a method to decide which vertice are grouped. 

3. iBFS's frontiers will become large as grouping multiple instances; thus, we need to reduce memory consumption for frontier queues.

## Solution

1. In the expansion phase, the joint status array stores status for every BFS instances. It applies a warp vote to communicate within a thread warp, deciding whether to push the vertex into the queue or not. In the inspection phase, it creates a cache to store neighborhoods. In this way, instances that ordered by its thread id could access global memory to check status in a coalesced way.

2. We could prove that the sharing ratio of frontiers determines the speedup. And if group A's speedup is greater than group B at current level, it is very possible that it maintains the advantage in the next levels. Following the proof, we form a strategy to group vertice that have outdegrees less than p but connect to a common vertex with outdegree greater than q. This strategy works for both top-down and bottom BFS.

3. We use bit-wise status array to lower the memory consumption. Also, we perform bit-wise operations for inspection, termination, and frontier identification, which futher acclerates the procedure.

## Question

1. Depth information lost by using bit-wise status array.