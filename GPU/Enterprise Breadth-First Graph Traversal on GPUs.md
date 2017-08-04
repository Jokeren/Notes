# Enterprise: Breadth-First Graph Traversal on GPUs

## Source

## Problem
BFS is the core of many graph applications. This paper propose a way to design high-performance BFS system that match the GPU hardware features.

## Motivation
1. Traditional frontier queue based BFS entails atomic operations that are costful on GPU. While the status array method do not has the limitation, it should maintain an array to track all the vertice, leading some threads idle. 

2. There is a large variance among the outdegrees of frontiers. Therefore, assigning a fixed number of thread for each level is inefficent because the running time is determined by the heaviest workload.

3. Bottom-up BFS has its advantage in early termination when unvisited vertice are small. But we still have to make the process GPU-aware.

## Solution
1. Streamlined scheduling is designed to avoid atomic operations and maximam the memory access speed. For the top-down workflow, it incurs sequential access on expansion where a prefix-sum is applied. For the direction-switching workflow, the inspection phase will be sequential. For the bottom-up switching, it only removes visited vertice out of the queue.

2. It divides the workloads into different level and apply different number of threads to each workloads, from a single thread to a whole grid, which achieves the most performance gain.

3. When a large number of hub vertice need to be visited, we should switch to bottom-up BFS. By caching hub vertice in shared memory, it could further accelerate the procedure.

## My Questions&Notes
1. Doubt about the copying procedure

