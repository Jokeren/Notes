The paper presents a exhaustive survey on the performance of concurrent primtive and applications on multi-core platforms. It dissects applications into a hierarchy by its complexity, from the lowest level load & store operations to the highest level concurrent software. Applications are tested on both single-socket and multi-socket systems.

ssync a comprehensive benchmark software designed for the test. The authors provide thorough discuss on the platform characteristic that impacts a specific application, how could we improve the performance on the software level, and what's the impliciation for users.

In the end, it concludes several rules for design concurrent utilities. Multi-socket processors generally have longer latency when data is shared across scokets, no matter it is load & store or atomic operations. Therefore, whenever designing locks or software, it is critical to keep data locally. Simple locks are powerful when contention is low.

The authors present insight on designing scalable hardware to support concurrent software.

The authors propose a improvement to alleviate unnecessary broadcast of invalidations on AMD's Opteron processor.

The authors test applications on different scenarios, either highly or slightly contented, provide good suggestions for application developers.

Lock-free techniques are not discussed in the application level, thought I know the author later published another paper dedicated for lock-free data structures. Also, hardware transaction is missed.

Incorporate message passing into this paper is a little redundant or unrelated. The performance of message passing is implementation dependent.

Power consumption has not been considered in this paper.
