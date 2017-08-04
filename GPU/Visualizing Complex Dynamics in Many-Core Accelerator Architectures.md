## Source

ISPASS'10

http://ieeexplore.ieee.org/document/5452029/

## Problem

GPUs involve massive parallelism at runtime that produces complex dynamic bahaviors. Using performance counter to quantify a entire program might be too general. Consequently, programmers should spend a large amount of effort in finding outstanding metrics related with programs and architectures. 

## Motivation

The need of performance visualization has long been addressed, while there is no open source software that serves to visualize dynamic behavior of CUDA and attribute performance statics to lines of codes.

## Solution

1. Interconnect starvation

Using figures to show dynamic IPC of each SM, comparing between different interconnect strategies.

2. DRAM contention

Using a figure to describe global memory write for each DRAM channel at every cycle.

3. CUDA source

- bank conflict: using a figure to show shared memory access cycles per warp.

- non-coalesced global memory access: showing the number of non-coalesced accesses per line.

- performance bottleneck: showing which lines in the source code were executed during a given period. It is useful even when no performance metrics has been identified.