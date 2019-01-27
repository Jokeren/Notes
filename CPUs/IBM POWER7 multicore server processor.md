## Source

IBM Journal of Research and Development(Volume: 55 , Issue: 3 , May-June 2011)

https://ieeexplore.ieee.org/document/5757896

## Problem

Improve the socket-level, core-level, and thread-level performances significantly over POWER6 while reducing core area, remove external L3 cache, and fit into the same socket as POWER6.

## Motivation


## Solution

1. eDRAM
eDRAM has larger density than sDRAM but higher speed than traditional DRAM. Thus, eDRAM is a key technology that allows the large 32-MB-shared-L3 cache to be on-chip. In summary, on-chip eDRAM in POWER7 provides one-sixth the latency, twice the bandwidth, compared with off-chip eDRAM, and one-ﬁfth standby power in one-third the area, compared with SRAM.

2. Out-of-order execution and branch prediction
In POWER7, the register rename structure for the GPR, (FPR), and (VR) are all merged into one uniﬁed rename structure with a total of 80 entries, matching the maximum number of outstanding nonbranch instructions between instruction dispatch and completion. In addition, in earlier machines, the issue queues for ﬂoating-point instructions and ﬁxed-point have been combined to reduce the area and power, called uniﬁed issue queues (UQ).

The POWER7 core uses separate mechanisms to predict the branch direction and the branch target address. The POWER7 IFU supports a three-cycle branch scan loop to fetch 32 bytes from the instruction cache. Since it takes three cycles to obtain the next fetch address, for two of these cycles, there is no fetch for the thread. However, other active threads can utilize these cycles and do instruction fetch in the SMT modes.

3. SMT4
A partitioned approach to the SMT4 design was incorporated. A pair of threads is supported from one physical general-purpose register (GPR) ﬁle that feeds one ﬁxed-point unit (FXU) pipeline and one load/store unit (LSU) pipeline, and another pair of threads is supported from a separate physical GPR ﬁle that feeds a separate FXU pipeline and LSU pipeline.

## My Questions&Notes

