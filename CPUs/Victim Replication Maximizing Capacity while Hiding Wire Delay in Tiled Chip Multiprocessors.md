## Source

ISCA'05

https://ieeexplore.ieee.org/document/1431568/

## Problem

In current CMP design, most L2 caches have a simple ﬁxed-latency to access. Using the worst-case latency results in unacceptable hit time in future processors with more cores and larger caches.

## Motivation

1. Tiled design

Tiled CMPs scale well to larger processor counts.

2. Victim replication

Multiple copies of a cache line can co-exist in different L2 slices of the shared L2 cache. Each copy of an L2 cache line residing on a tile other than its home tile is a replica. In essence, replicas form dynamically-created private L2 caches to reduce hit latency for the local processor. 

## Solution

1. CMP design

If a primary cache line is evicted because of a conﬂict or capacity miss, we attempt to keep a copy of the victim line in the local slice to reduce subsequent access latency to the same line. The L2VR replication policy will replace the following classes of cachelines in the in descending priority order: (1) An invalid line; (2) A global line with no sharers; (3) An existing replica. L2VR has a small area overhead over L2S because of keeping a tag to distinguish replicas from regular L2 lines. 
 
2. Experiments

SpecINT2000 is used in the experiments. The multi-threaded tests show that L2VR not only has the lowest average latency but also causes less network traffic than L2P. In the single-threaded tests, L2VR has high replica rates. L2VR is usually comparable or better than the L2P scheme, combining the advantages of fast accesses to the local L2 slice with a large on-chip backupcache. We consider the effect of backupcache because a single thread might be moving between CPUs scheduled by the OS.

## My Questions&Notes

My guess is that by binding a thread to one specific core, L2VR will has the same performance as L2P in the single-threaded environment.