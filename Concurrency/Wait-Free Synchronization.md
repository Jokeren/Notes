The paper comprehensive introduces both the concepts and examples of wait-free synchronization. It first proves there's no wait-free implementation from an object to another that has a higher consensus number. Then, it discusses the consensus number of various utilities, such as test&set and concurrent data structures. Lastly, it shows how universal objects could construct a wait-free implementation of any object.

The paper is a milestone in the development of concurrent data structures. It clearly defines the relationship between linearizability and wait-free condition. It points out the basic principles to construct wait-free objects. It proves there exists a universal object for constructing wait-free objects.

I was astonished by the idea of wait-free and linearizability. Being that, I have nothing to blame. However, I would like to stress out that the paper only discusses the availability of a wait-free object, abandoning all the practical issues. We do not know the lower bound time complexity of a wait-free object in comparison to a sequential object. Probably, we can assume atomic operations take a constant time to update and derive a formula for the time spent under a given number of threads.

Model performance upper-bound for wait-free objects?
