##Source

ISPASS'10

http://ieeexplore.ieee.org/document/5452013/

##Problem

GPUs have a different architecture from traditional CPUs. For architecture and compiler developers, it is essential to fully understand detailed of modern GPU designs.

##Solution

1. Cache

Cache way, set, and size could be deduced from repeated and strided access. 

2. Clock values

Clock registers are per-TPC.

3. Arithmetic pipeline

We should test int, float, and double precisions to derive their latency and throughput.

4. Divergence and reconvergence

When threads within a warp diverge, the warp serially executes each path taken from the last program order to the first and then converge. Also, we could set a reconvergence to test whether threads within a warp are executing in a SIMT way or not.

5. Synchronization

__syncthreads only takes effect across multiple warps.

6. Register File

The number of registers used by a thread is rounded to a multiple of four. The number of threads of a block is quantized to a multiple of 64, letting each thread access a logical bank.

7. Cache

Cache has two three main purposes: TLB, data, and instruction. Texture cache has two levels, where the L2-cache is TPC dependent. L1 TLB is fully-associated, holding 16 lines of 512KB TLB line size. Constant and instruction has three cache levels, of which L2 and L3 are unified.

