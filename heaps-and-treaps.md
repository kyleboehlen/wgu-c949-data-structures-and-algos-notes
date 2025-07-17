# Heaps and Treaps

## Max-heap

A max-heap is any tree, but typically a binary tree, where the parent node of any given node is greater than or equal to the node. Another way of saying this would be that any node's children must be less than or equal to that node.&#x20;

What is a max heap for? Think about a priority queue. The only thing the computer cares about is getting the highest value node, or the highest priority task, and processing it. By definition the root node of a max-heap will always be the highest value node.

### Insertions

When inserting a node in to a max-heap you insert it in to the last level, the deepest level, of the max-heap from left to right. You then swap places with the inserted node and it's parent as many times as it takes until the node's parent is greater than the inserted node. This upward movement is called percolating. See an example of inserting a node, node 85, in to the max heap below:

### Removals

Removals happen like reverse insertions. They start by removing the root node and replacing it with the furthest right node in the deepest level of the tree. Then the node is swapped with it's greatest value child until it has no children that are greater than that node.

### Arrays

Heaps are typically stored in arrays. That way they can be traversed in order. See the example heap in tree form, and in the corresponding array below:

