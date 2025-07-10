# 000 Introduction

## Data Structures

<table><thead><tr><th width="139">Data Structure</th><th>Description</th></tr></thead><tbody><tr><td>Record</td><td>A record is the data structure that stores subitems, often called fields, with a name associated with each subitem.</td></tr><tr><td>Array</td><td>An array is a data structure that stores an ordered list of items, where each item is directly accessible by a positional index.</td></tr><tr><td>Linked list</td><td>A linked list is a data structure that stores an ordered list of items in nodes, where each node stores data and has a pointer to the next node.</td></tr><tr><td>Binary tree</td><td>A binary tree is a data structure in which each node stores data and has up to two children, known as a left child and a right child.</td></tr><tr><td>Hash table</td><td>A hash table is a data structure that stores unordered items by mapping (or hashing) each item to a location in an array.</td></tr><tr><td>Heap</td><td>A max-heap is a tree that maintains the simple property that a node's key is greater than or equal to the node's childrens' keys. A min-heap is a tree that maintains the simple property that a node's key is less than or equal to the node's childrens' keys.</td></tr><tr><td>Graph</td><td>A graph is a data structure for representing connections amount items, and consists of vertices connected by edgtes. A vertex represents an item in a graph. An edge represents a connection between two vertices in a graph.</td></tr></tbody></table>

### Why do data structures matter?

All data structures have pros and cons. Picking the right data structure will be dependent on your needs, and the underlying data it is storing. Here is a quick example for why different data structures matter.

Lets say we need a data structure that can handle a lot of fast insertions. What happens if you pick an array?&#x20;

Here's an array with 3 elements:

\[A] \[D] \[Z]

What happens when we want to insert element B?

First we create a new index at the end of the array:

\[A] \[D] \[Z] \[\_]

Then each element after the index we are inserting the element needs to shift:

\[A] \[D] \[\_] \[Z]

\[A] \[\_] \[D] \[Z]

Finally, we can insert the new element:

\[A] \[B] \[D] \[Z]

What would it look like if we had the same data in a linked list?

A->D

D->Z

Z->null

To insert element B first we would create the element with a pointer to the next node in the list

A->D

D->Z

Z->null

B->D

Then we simply update the pointer for the node before the new element

A->B

D->Z

Z->null

B->D

No shifting of elements required. For a situation that requires a very fast insertion, this is why a linked list could be a better choice over an array.

## Algorithms

### The 10 Types of Algorithms

**1) Brute Force**

A brute force algorithm is very simple and extremely straightforward. It tries every solution until it finds the correct answer. It is inefficient.&#x20;

**2) Greedy Algorithm**

A greedy algorithm selects the best option given each situation provided, regardless if the overall outcome is optimal. It is a simple, intuitve algorithm. Its runtime complexity is also pretty reasonable. In order for a greedy algorithm to give you the best outcome overall the problem must have the following 2 properties.

1. Choosing the best option at each phase can lead to an overall optimal solution
2. The optimal solution is made up of an optimal substructure, meaning the optimal solution to a problem is composed of the optimal solutions to every sub-problem.

In order to show you how a greedy algorithm works, let's show 2 examples where a greedy algorithm wouldn't work.

— TODO

**3) Divide and Conquer Algorithm**

**4) Dynamic Programming Algorithm**

**5) Backtracking Algorithm**

**6) Recursive Algorithm**

**7) Searching Algorithm**

**8) Sorting Algorithm**

**9) Hashing Algorithm**

**10) Machine Learning Algorithm**





