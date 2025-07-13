# 002 Stacks and Queues

## Stack

A stack is an abstract data type that only allows values to be inserted and removed from the top. This is referred to as a last in first out abstract data type. Inserting to the top of a stack is referred to as pushing, removing from the top is referred to as popping, and checking the top value without removing it is referred to as peeking. A stack can be implemented with a linked list, array, or vector.

### Linked List

When using a linked list to implement a stack abstract data type the head node will be used as the top of the stack. Seems counter intuitive to me, but it keeps the time complexity at O(1) because the head is the easiest node to access. I guess this makes sense. If you're using a singly-linked list you would need to traverse the entire list to figure out what the new top of the stack would be, and if you're using a doubly-linked list then you'd need to update 2 nodes instead of only updating the head pointer and possibly the new node. Fair enough.

### Array

When using an array to implement a stack the top of the stack will be array\[length - 1]. An array stack can be either bounded (has a max length) or unbounded (does not have a max length) but the underlying array must also be able to re-allocate infinitely if the stack is unbounded.

## Queue

A queue is an abstract data type where values are inserted at the end of the queue, and removed from the front. This is a first in last out abstract data type. Adding a value to the end of the queue is referred to as enqueue, and removing a value from the front of the queue is referred to as dequeue. Queues can also be implemented with either a linked list, or array.

### Linked List



### Array

## Deque

A deque (pronounced deck) is a double sided stack. It has the same operations as a stack, but you must specifiy whether the operation is happening at the front or back of the stack. I.E. pushBack, popFront, peekBack, etc.
