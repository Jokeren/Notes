## Source

A Primer on Memory Consistency and Cache Coherence

https://www.morganclaypool.com/doi/abs/10.2200/s00346ed1v01y201104cac016

## Problem

Shared memory behaviors must be defined, since modern cores may reorder memory accesses, including store-store, load-load, load-store, and store-load.

## Motivation

1. The Single Writer–Multiple-Reader (SWMR) invariant

It ensures that at any (logical) time for a memory location with a given address, either (a) one core may write (and read) the address or (b) one or more cores may only read it.

2. Memory Consistency Model

Coherence applies on a per-block basis, whereas consistency is defined across all blocks. 

3. Sequential Consistency (SC)

(1) 
If L(a) <p L(b) ⇒ L(a) <m L(b)  /* Load→Load   */
If L(a) <p S(b) ⇒ L(a) <m S(b)  /* Load→Store  */
If S(a) <p S(b) ⇒ S(a) <m S(b)  /* Store→Store */
If S(a) <p L(b) ⇒ S(a) <m L(b)  /* Store→Load  */

(2) Every load gets its value from the last store before it (in global memory order) to the same address.

4. Total Store Ordering (TSO)

TSO excludes Store->Load constraint in SC model.

In addition, every load gets its value from the last store before it to the same address:

Value of L(a) = Value of MAX <m {S(a) | S(a) <m L(a)} /* Change 2: Need Bypassing  */
Value of L(a) = Value of MAX <m {S(a) | S(a) <m L(a) or S(a) <p L(a)}

In a word, with by-passing, there's no difference between the same address ordering between TSO and SC.

## Solution

1. Sequential Consistency

We can implement SC by a multi-tasking processor, where thread T1's instructions execute on core C1 until a context switch to thread T2.

we can also implement SC by a switch. Each core presents one memory operation to the switch at a time, and each core can use any optimizations that do not affect the order in which it presents memory operations to the switch.

Lastly, sequential consistency can be implemented on the top of cache coherence.

2. TSO Consistency

Most current TSO implementations take an SC implementation and insert write FIFO buffers.

## My Questions&Notes
