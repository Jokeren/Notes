## Source

CF'07

https://dl.acm.org/citation.cfm?id=1242531.1242541

## Problem

A large class of applications to become memory-bound because of the performance differential between memory systems and microprocessors. To address the problem, a large portion of computers utilize a cache hierarchy to hold data from memory. However, many irregular applications cannot be accelerated by cache because of lacking locality. Thus, it becomes imperative to consider an alternative architecture for irregular and data-intensive applications.

## Motivation

In particular, multithreaded architectures, designed to tolerate memory access latencies by switching context between threads, offer a very appealing alternative for data-intensive applications. The Cray Threadstorm (MTA-2) and Sun Niagara processors are two examples of modern multithreaded processors

## Solution

MTA-2 has 128 hardware thread-streams on one instruction pipeline. The MTA has a flat, cache-less, hashed, shared-memory architecture where all the resources are interconnected in a modified Cayley graph.

Sun Niagara supports 32 concurrent threads, where every 4 threads are grouped into a thread group and share a processing core. A processing core has a single-issue pipeline, a 4-way 16KB instruction and a 4-way 8 KB data cache.

Benchmarks and real-world applications are used to evaluate two architectures.

1. Bandwidth

The MTA exhibits a processor dependent bandwidth increase that is less dependent on the type of kernels as this is the case for Niagara. 

2. Ordering

Ensuring ordering is relatively simple for Niagara than MTA, as Niagara makes apparent cache use for the “critical, lock, ordered” and “atomic” constructs whereas MTA initially performs memory polls before it exploits its memory signaling forwarding capabilities.

3. Power System State Estimation

Since one FPU is shared among eight cores, Niagara stops to speedup at four threads. Since the maximum parallelism is constrained by that available in the data-parallel loop sections, there is a bottleneck creating the data-parallel tasks on MTA-2.

4. PDTree 

PDTree is a memory-bound, integer-based application with minimal floating-point operations (only used for timers) and as such is a good match to the capabilities of both platforms which are not oriented towards floating-point computation. 

## My Questions&Notes

I felt this paper needs to polish its organization and experiments part. It has to cut off a few paragraphs about how they modified the two real-world applications. Besides, in the introduction part, it should point out benchmarks are equally importantly as real-world applications. The first real-world application---PSE, does not seem to be "irregular" at all, because elemented are stored in an array and accessed sequentially. And I do not maintain that data-intensive is equvalient with irregular. How do we define applications that are accessed sequentially but have a small number of computations?
