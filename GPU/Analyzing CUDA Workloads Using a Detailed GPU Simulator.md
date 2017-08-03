##Source

ISPASS'09

http://ieeexplore.ieee.org/document/4919648

##Problem

GPUs offer order of magnituide computing power more than contemporary CPUs. Thus, understanding GPUs characteristics is vital for improving the performance of parallel applications. This paper run sample applications on a GPU simulator, describing the impact of micro-architectural deisgns.

##Solution

Draw various kinds of figures, such as instruction classification, IPC, occupancy, and speedup to derive performance bottlenecks.

1. Interconnect

Different topology: Butterfly networks, crossbar, 2D torus, ring and mesh, which do not change performance of most benchmarks. The performance is more sensitive to bandwidth than latency.

2. CTA distribution

GPUs launch an abundance of parallel CTA on shader cores. Allowing more CTA running on the same core provides latency benefits, while increasing memory burden and register resource usage.

3. Memory access coalescing

By examine memory utilization and efficiency, we figure out a simple DRAM controller suffers from performance reduction with bank conflicts.

4. Cache

Applications that make extensively use of shared memory do not rely on cache size, while others gain speedup with the growth of cache.