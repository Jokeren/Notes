#Efficient Synchronization Primitives for GPUs

##Source

http://arxiv.org/abs/1110.4623v1

##Problem
Previous GPU primitives are insufficient to handle the discrepancies between GPU and CPU hardware.

##Solution
From the benchmark, there are three important characteristics for the design of primitives:

1. Atomic:Volatile memory access performance ratio.

2. Contentious:Noncontentious volatile access ratio. 

3. Do atomic units with a non-empty queue hold a line hostage? (L2 cache or not. Nvidia add L2 cache into the Fermi infrastructure)

Due to these principles, the implementations of different primitives should be various on architecture. We have to provide a high-level api that hide the nuance.

##Experiments

The experiments saturated the computing resources by lauch hardware limited blocks and utlize all the threads. It performs 1000 instances of an operation to measure the performance.

##My Questions&Notes
1. Practical application