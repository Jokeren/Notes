#A Pragmatic Implementation of Non-blocking Linked-Lists

##Source
15th International Conference, DISC 2001 Lisbon, Portugal, October 3¨C5, 2001 Proceedings

http://link.springer.com/book/10.1007/3-540-45414-4?no-access=true#page=310

##Problem

Present a non-blocking implementation of concurrent linked-list, which supports linearizable insert and delete operations.

##Motivation

Using atomic instructions, it is convenient to eschew locks, and build scalable fundamental components for large distributed systems.

##Solution

The running example suggest that the insert operation could be finished by a single CAS, while the delete operation itself could not realize extra nodes inserted.

Hence, to overcome the problem of nodes loss, the crux is to adopt two separated CAS *casMark* and *casNext* in place of a single one. 

**Insert algorithm**
First locate the previous node by *search* routine, then insert the node by CAS. If unsucceed, continue to locate.

**Delete algorithm**
Like the insert operation, it also locates the target node at the beginning. It removes the target node within two steps:

 1. Marks the *next* pointer of the previous node. If succeed, breaks the loop. We could define this as a *linearization point* in relaxed memory consensus.
 2. Removes the node, if unsucceed, it indicates that other thread *helps* to remove the node. 

**Search algorithm**
The search algorithm ensures *invariants* proposed in section 4. 

1. *prev* node must be immediate predecessor of the *next* node.
2. Both *prev* node and *next* node are unmarked.
3. Key order constraints.

##My Questions&Notes

1. Change the linearization point. Just as which described by Faith Ellen in Non-blocking BST, we might change the linearization point to the *physical deletion* point. 

2. In proof section:

> Each time B3 or B4 is taken the CAS at C2 or C4 has failed. 

I think B4 is unrelated with C4, instead it is induced by C3.

3. The `proof sketch` section is very clear. 