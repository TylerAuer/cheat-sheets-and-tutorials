# Notes About Data Structures and Algorithms

## Queue
An ordered collect of items, like a line, where the first element in is the first one out. **FIFO**. Picture this like a line at a store: first person in line is the first one who is called to the counter. 

### Interview Questions

1. Implement this as a JS Class
2. "Weave" together to queues by alternating the first from each queue
3. Implement a Queue using stacks (poping items from one stack to another reverses it, effectively making it a queue. Go from there.)

## Stack

An ordered collection of items, like a pile, where the first element in is the last element out. **FILO**. Picture this is a stack of records. The last on put on is the first one picked up off the pile.

### Interview Questions

1. Implement a queue using two stacks. See above. 
   **Solution:** Moving a stack onto another stack reverses the stack essentially making it a queue

## Linked List

A list of nodes where each node contains some data and directions to the next node. The first item in the list is called the *head node* and the last is called the *tail node*. The refernce in the tail node is null.

### Interview Questions

1. Determine if a linked-list is circular (if the is no node pointing to `null`) 
   **Solution:** Use two variables, fast and slow to move through the linked list at different rates (+1 and +2). If they ever point to the same node then the list is circular
2. Find the midpoint of a linked list
   **Solution:** Use two variables, fast and slow to move through the linked list at different rates (+1 and +2). When fast gets to the end, slow is at the midpoint
3. Find the *n*th from the last node.
   **Solution:** Use two variables, ahead and behind to move through the linked list. Start `ahead` *n* indexes ahead of behind. When `ahead` reaches the end, `behind` is at the correct index

## Tree

Each location on the tree is called a **node**. Each node contains data and a list of the nodes children (not recursively). "Parent, child" is used to describe this relationship. Nodes with the same parent are called siblings. Trees have a `root` node which is the top / highest level of the tree. It's the equivalent to a `head` in a linked list

Unlike linked lists, the `add()` and `remove()` methods live on the `Node` not on `Tree`. Imagine if you tried to call `add()` on the tree, how would you know where to add the new node. Because the structure is more varied, we modify the nodes more directly.

**Tree Traversal** is iterating through every element in the tree. This can be done **depth-first** or **breadth-first**.

**Breadth-first:** Iterate level by level

**Depth-first:** Go into the children of each node when we encounter them before moving to the sibling.

**Binary Tree** - Each node has, at-most, 2 children.

**Binary Search Tree** - Each node can have up-to 2-children. They are called the left-node and the right-node. The data in a node is also restricted: the left-node is always less than the data and the right-node is greater than the data. The left- and right-nodes are usually assigned to properties instead of as an array. The data is usually called value or key.

### Interview Questions

1. Implement a depth-first search and a breadth-first search of a tree.
   **Solution:** Have a placeholder array into which go the children of each node you encounter. For a breadth first tree, the children go in at the end (FILO) and for a depth first tree, the children go in at the start (FIFO)
2. Determine the width of each level of a tree
   **Solution:** Very similar to above. Start with array for the children like above, but have it be filled with `[0, null]` where `null` is a marker between levels of the tree. When you reach `null` have your width counter/tracker move to the next level.
3. Validate a binary search tree (confirm that the left node is always less than the right node)
   **Solution:** Recursively call a validator function on each node with two additional parameters `min` and `max`. Whenever you are about to move to a left child, set the max to the current node's data, since that is the max value the left child can be. When you move right, set the min. Call this recursively, returning true all the way up or returning false if anything is out of place.