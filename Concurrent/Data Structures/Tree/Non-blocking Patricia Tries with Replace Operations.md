#Non-blocking Patricia Tries with Replace Operations

##Source
ICDCS '13 Proceedings of the 2013 IEEE 33rd International Conference on Distributed Computing Systems

http://dl.acm.org/citation.cfm?id=2549695.2549733&coll=DL&dl=GUIDE&CFID=558601920&CFTOKEN=46023158

##Problem

Non-blocking Patricia Tries is widely used in practice, thus allowing it support concurrent access is very essential.

##Motivation

1. Patricia trie is a simple unbalanced tree.
2. Though the Patricia trie unbalanced, its height is bounded without balancing.
3. The implementation renders good performance under both uniform and non-uniform environment.
4. The `replace` operation is very interesting, which modifies two parts of the trie in a single operation.

##Solution

This work extends the original solution discussed in Ellen's paper(see 2010 PODC, nonblocking BST, we would revisit its proof in the future). Further, it transform the update scheme in a more uniform way to make it more applicable.

**Insert algorithm**

find the target node, or reach an internal node whose label is not a prefix of the search key. It makes a copy of the target node, and creates new nodes, then replaces the old node.

**Remove algorithm**

It reaches the target node in the same paradigm as the Insert algorithm. It tries to move the pointer from the target node to the sibling node.

**Replace algorithm**

First locate the delete node and insert target. Then it flags the nodes involved in the delete operation, including the leaf node, then flags the insert area. After flagging all these nodes, it first inserts the new node, and then physically removes the leaf node. 

**Search algorithm**

find the target node, check whether it is deleted.

##My Questions&Notes

1. Actually we could use quadtree to retrieve nodes more efficiently
2. edge-oriented multi-way tree
3. chain deletion
4. move operation
5. pre-allocation
6. decoupling