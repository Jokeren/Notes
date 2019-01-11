## Source

Journal Computer Volume 30 Issue 9, September 1997 

https://dl.acm.org/citation.cfm?id=620806

## Problem

However, relying a single thread to exploit parallelism for applications is impossible. Instead, achieving parallelism usnig a software approach is more promising because of emerging multi-tasking applications, such as multimedia, scientific computing, and Microsoft Windows NT.

## Motivation

First, wire delay stays nearly constant or increases as wires become finer and die sizes are expanding as designers strive for higher performance. As a result, the delay of the longest wires on a chip is improving two to four times more slowly than gate delay.

Second, a long wire in a circuit can now affect the processor’s cycle time if it happens to be on a critical timing path.

To avoid long wires, CPU sections need to be rearranged or piplelines need to be elongated. In this way, our increased ability to create complex architectures is outstripping our ability to validate them.

## Solution

SMT, though highly utilizes execution resources, simply looks like a conventional wide-issue superscalar, and drives the billion-transistor chip design complicated. 

1) SMT's area increases quadratically with the core's complexity. 
2) They can require longer cycle times, which could be hidden by deep pipelining. But it turns out to bring misprediction penalties.
3) Design and verification costs will increase since they must be designed and verified as single, large units.
4) SMT requires primary cache bandwidth than CMP.

CMP, which is relatively easy, is preferable.

The CMP architecture uses a group of small, identical processors. Cores are completely independent and tightly integrated with their individual pairs of caches.

Four applications are used to compare the performance between SMT and CMP. For applications with large amounts of thread-level parallelism, CMP outperforms SMT. But for applications without thread-level parallelism, SMT outperforms CMP.

Though SMTs can almost always use execution resources more efficiently than CMPs, more execution units can be included in a CMP of similar area, since less die area need be devoted to the wide-issue logic.

## My Questions&Notes

1. "The number of registers in each structure must increase proportionally to the instruction window size."

There are some physical registers always contains committed architectural register values, so the number of registers do not have to increase proportionally.