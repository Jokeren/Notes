Software Transactional Memory for Dynamic-sized Data Structures

The authors propose a new design for software transactional memory (STM) which supports dynamic-sized data structures and guarantees obstruction-free progress. With locks, a thread preempted while holding a lock will obstruct other threads. In contrast, obstruction-free means threads run by itself will not be prevented by threads that are halted. Unlike previous STM proposals, the STM model in this paper allows dynamically allocated transactions and transactional objects. The authors implement their STM model in java and present a few examples including concurrent linked-list and red-black tree to show the effectiveness.

STM brings much a simpler programming model to the concurrency world. We can use STM to quickly implement complex pointer-based data structures and achieve faster speed than coarse-grained locks. 

Beyond the simpleness, STM-based data structures are easy to write and prove, though in some cases, fine-grained locks and lock-free designs may render faster speed.

Obstruction-free is often not enough. In today's world, SIMT processors are widely adopted. A Power8 processor has 8 SIMT threads for each core and 96 threads in total, which indicates a high possibility that another will preempt a thread and let it be scheduled later. In this case, we should let the contention manager be more intelligent, achieving lock-free or even wait-free progress.

The STM model proposed in this paper suffers many performance problems. Even though it solves a few unnecessary conflicts, such as reader operations in concurrent with write operations, it's still heavy and requires many additional CAS operations.

Because Java has an explicit memory manager, we do not have to implement another for STM. However, for other languages, we need to specify how memory allocation and deallocation behaviors affect STM. 
