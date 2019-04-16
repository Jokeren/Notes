The paper introduces features about IBM Blue Gene/Q's memory system, which are designed for multi-versioning and conflict detection. Two cutting-edge techniques are integrated into Blue Gene/Q--transactional memory and speculative execution. Speculative execution parallelizes a sequential program by split a sequential region into two and letting a younger thread wait for older threads to commit. In transactional memory, transactions are executed in isolation, tons of tags are records on the memory system to record the states.

IBM has also developed specific language programas to help to utilize the above two features. We can use #pragma tm_atomic for transactional memory regions and #pragma speculative to express speculative execution.

Last, a set of special atomic operations are designed o support multi-producer and multi-consumer queues. Some interesting ones are larx and stcx, which pull data closer to cores and limit fetching latency.

Blue Gene/Q is the first commercial processor that implements general purpose speculative execution. And performance results show that speculative execution continues to scale up to 16 threads.

Blue Gene/Q is the first commercial processor that implements hardware transactional memory.

I doubt that the benefits of implementing both speculative execution and transactional memory. Is there are any benefits to support both of them? I do not know, but definitely, it requires a large amount of research and development cost. And I would argue that the benefits of speculative execution can be achieved by software level optimization plus transactional memory.

The authors did not mention anything about performance when using both transactional memory and speculative execution. Since both techniques require states recording, memory burst may happen during execution.

Nowadays there are a series of programming models, while IBM may have made OpenMP efficient, other models may not. Therefore, transforming other models to OpenMP still has a cost.
