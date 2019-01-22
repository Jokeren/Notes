## Source

ISCA'10 Proceedings of the 37th annual international symposium on Computer architecture 

https://dl.acm.org/citation.cfm?id=1816018

## Problem

Next generation microarchitectures will run a mix of applications with different memory needs.

## Motivation

Existing adaptive memory hierarchies use either centralized structures that limit the scalability or software based resource allocation that increases programming complexity. 

Cache partitioning has a signiﬁcant performance impact in runtime execution and that dynamic conﬁgurations can adapt to the program’s time-varying phase behavior and improve performance. For instance, streaming applications do not reuse a large amount of data.

## Solution

1. ElasticCC

The ElasticCC framework consists of several independent L2 cache memories that are logically divided into a shared and a private region that compete for the cache space. This allows the creation of big local private caches if all applications have similar cache requirements and a big shared cache if only a few take advantage of extra cache space.

2. Repartition (node level)

The Cache Repartitioning Unit is responsible for dynamically adjusting the amount of cache that is going to be private or devoted to spilled blocks. Repartitioning does not require the eviction of all cache blocks of the reassigned way since this would degrade performance unnecessarily. Therefore, new blocks will gradually replace the ones belonging to the other partition.

3. Block Spilling (across node)

Since not all nodes have the same shared cache space, the Spilled Block Allocator is responsible for deciding to which node a locally evicted block is spilled. Adaptive spilling allow spilling for both private and shared high utility applications.

4. Experiments

Experiments were run Simics simulator, and SPECOMP2001 was used in the experiments. ElasticCC has been compared against private cache and shared cache, which rely on a centralized cache or a centralized repartitioning unit.

The experiments show that ElasticCC renders the best performance results in all the benchmarks. The only conﬁguration where performance is not similar to the ideal conﬁguration is Swim-Ammp, where ASR gets better performance. In this case both benchmarks beneﬁt from the larger cache space and none of them leaves unused cache space.

The experiments also illustrated the effects of adaptive spilling to optimize shared space among multiple applications and within a single application's different phases.

## My Questions&Notes

Although ECC performs well on a simulator platform, I am worried about how it's real performance will be when it's implemented. Because it has added a large portion of units to conduct memory coherence. Will the on-chip network traffic become a problem?