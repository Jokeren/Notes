# GPU Multisplit

## Source

PPoPP '16 Proceedings of the 21st ACM SIGPLAN Symposium on Principles and Practice of Parallel Programming

http://dl.acm.org/citation.cfm?id=2851169

## Problem
*Multisplit* is a broadly useful parallel primitive that permutes its input data into contiguous buckets. A great number of applications invoke multisplit. It is the first step to build kd-tree, suffix array, and hash-table; it is also an important building block of parallel single-source shorted path.

## Motivation
Multisplit has no need to order items within a bucket. Therefore, when the number of buckets is small, we could adopt other methods for an efficient implementation.

## Background

**reduction**
A *reduction* inputs a vector of elements and applies a binary associative operator (such as addition) to reduce them to a single element; for instance, sum-reduction simply adds up its input vector.

**scan**
The *scan* operator takes a vector of input elements and an associative binary operator, and returns an output vector of the same size as the input vector. 

**compaction**
*Compaction* is an operation that filters a subset of its input elements into a smaller output array while preserving the order.

## Solution
**recursive scan**
On each round we split key elements into two groups of buckets, rendering at most logm rounds.

**radix sort**
Sort based methods are independent of the number of buckets. The radix sort method compares keys from the LSB(lowest significant bit) or the MSB(most significant bit). However, radix sort performs more works than multisplit by sorting elements within a bucket.

**reduced-bit sort**
It first calculate the label for each key, then combines the originial key into the label for the radix sort.

**histogram**
It calculates a formula to generate the final position of each element, reorders them within a warp, and put them into the output finally.

All the above methods could be described as three stages:

1. Local scan. The histogram method counts the number of elements in a wrap that fall into each bucket.
2. Global scan. The histogram method counts the total number of elements within other subproblems before its final positions.
3. Local scan. The histogram method local offset element.

## Experiments
The scan-based method outperforms others when the number of buckets is less than 32--the warp size. With the increment of the warp size, the reduced-bit shows the best performance. 

## My Questions&Notes
1. Demonstrate the effectiveness of the method in real applications?
2. The results illusrates that we should avoid global operations in GPU programming. But I think a specific performance model should be proposed for a more convincing statement.
