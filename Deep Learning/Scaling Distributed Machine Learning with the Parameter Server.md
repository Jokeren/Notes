## Source

OSDI'14

https://www.usenix.org/conference/osdi14/technical-sessions/presentation/li_mu

## Problem

Building a scalable, fault-tolerant, and user-friendly machine learning system.

## Motivation

In industry area, the amount of training data is growing at a rapid speed, which give rise to huge number of parameters in complex models. Related systems, such as YahooLDA, Petuum are insufficient to meet the increasing growth of both data and model.  Likewise, for these general-purpose distributed system, like Mahout, MLI, both adopt iterative MapReduce framework, the inefficiency lies in their application oriented design and consistency models. Finally GraphLab relies on coarse-grained snapshot mechanism which impede its scalability.

Piccolo is a previous parameter server framework, but it lacks machine learning specific optimizations: message compression, replication, consistency model.

## Solution

1. (key, value)-vectors:

	Store non-exist keys as zero to accelerate computing by multi-threaded libraries such as BLAS, LAPACK, and ATLAS

2. Range Push and Pull

	A flexible api for sending range keys.

3. Asynchronous Tasks and Dependency

	Parameter weights are updated according to specific consistency models. The author lists out three typical task dependency models: **Sequential**, **Eventual**, **Bounded Delay**.

4. Filter

	A **KKT** filter is used to filter related parameters out of the original vector. In the talk, the author indicates that it could reduce 95% amount of band width.

5. Range Vector

	Rather than associate each key with a *clock*, we could represents the keys which have the same timestamp by a single value.

6. Consistent Hashing

	Handle key range in servers.

7. Aggregate Replication
	
	Reduce bandwidth by aggregating (summing) from the workers first. The extra cost in postpone the sending process could be compensated the relaxed consistency model.

## My Questions&Notes

The author proposed a highly scalable, easy-to-use and fault-tolerant distributed machine learning system. The major advantage of its efficiency is contributed by its relaxed consistency model.

From my perspective, though the author declares that such a design is suitable for general machine learning systems, I highly doubt whether it is efficient for deep learning systems where multi-gpu are existed in a single machine. To solve the problem, I have to reread the Adam framework first. 
