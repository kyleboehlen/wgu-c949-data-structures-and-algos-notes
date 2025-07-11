# 000 Introduction

## Data Structures

<table><thead><tr><th width="139">Data Structure</th><th>Description</th></tr></thead><tbody><tr><td>Record</td><td>A record is the data structure that stores subitems, often called fields, with a name associated with each subitem.</td></tr><tr><td>Array</td><td>An array is a data structure that stores an ordered list of items, where each item is directly accessible by a positional index.</td></tr><tr><td>Linked list</td><td>A linked list is a data structure that stores an ordered list of items in nodes, where each node stores data and has a pointer to the next node.</td></tr><tr><td>Binary tree</td><td>A binary tree is a data structure in which each node stores data and has up to two children, known as a left child and a right child.</td></tr><tr><td>Hash table</td><td>A hash table is a data structure that stores unordered items by mapping (or hashing) each item to a location in an array.</td></tr><tr><td>Heap</td><td>A max-heap is a tree that maintains the simple property that a node's key is greater than or equal to the node's childrens' keys. A min-heap is a tree that maintains the simple property that a node's key is less than or equal to the node's childrens' keys.</td></tr><tr><td>Graph</td><td>A graph is a data structure for representing connections amount items, and consists of vertices connected by edgtes. A vertex represents an item in a graph. An edge represents a connection between two vertices in a graph.</td></tr></tbody></table>

### Why do data structures matter?

All data structures have pros and cons. Picking the right data structure will be dependent on your needs, and the underlying data it is storing. Here is a quick example for why different data structures matter.

Lets say we need a data structure that can handle a lot of fast insertions. What happens if you pick an array?&#x20;

Here's an array with 3 elements:

```
[A] [D] [Z]
```

What happens when we want to insert element B?

First we create a new index at the end of the array:

```
[A] [D] [Z] [_]
```

Then each element after the index we are inserting the element needs to shift:

```
[A] [D] [_] [Z]
[A] [_] [D] [Z]
```

Finally, we can insert the new element:

```
[A] [B] [D] [Z]
```

What would it look like if we had the same data in a linked list?

```
A->D
D->Z
Z->null
```

To insert element B first we would create the element with a pointer to the next node in the list

```
A->D
D->Z
Z->null
B->D
```

Then we simply update the pointer for the node before the new element

```
A->B
D->Z
Z->null
B->D
```

No shifting of elements required. For a situation that requires a very fast insertion, this is why a linked list could be a better choice over an array.

## Algorithms

A computational program specifies and input, a question about the input, that can be answered using a computer, and the desired output. An algorithm is the step by step process a computer would use to solve a computational problem. However, please note that an algorithm does not have to be written using a programming language.

Examples of Practical Applications of Algorithms

<table><thead><tr><th width="139">Field</th><th>Computational Problem</th><th width="257">Possible Algorithm</th><th data-type="content-ref"></th></tr></thead><tbody><tr><td>DNA Analysis</td><td>Given strands of DNA from two different individuals, what is the longest strand of nucleotides that both individuals have in common?</td><td><strong>Longest common substring problem:</strong> nucleotides in a string can be represented using A, C, G, and T. </td><td><a href="050-algorithm-examples/051-longest-common-substring-dna-analysis-example.md">051-longest-common-substring-dna-analysis-example.md</a></td></tr><tr><td>Product Search</td><td>If you were given a product ID, and an array of products, what is an efficient way of looking up the product details?</td><td><p><strong>Binary Search:</strong> an efficient way of searching through information where<br>A) you have an ordered list</p><p>and <br>B) the items can be accessed directly, for example via indexes in an array. </p></td><td><a href="050-algorithm-examples/052-binary-search-example-product-search.md">052-binary-search-example-product-search.md</a></td></tr><tr><td>Navigation</td><td>Given a starting and ending location, what is the fastest way to traverse the paths between those 2 locations?</td><td><strong>Dijkstra's Shortest Path:</strong> an algorithm that determines what the shortest path is between a starting vertex and each other vertex in a graph. </td><td><a href="050-algorithm-examples/053-dijkstras-shortest-path-navigation-example.md">053-dijkstras-shortest-path-navigation-example.md</a></td></tr></tbody></table>

### The 10 Types of Algorithms

**1) Brute Force**

A brute force algorithm is very simple and extremely straightforward. It tries every solution until it finds the correct answer. It is inefficient.&#x20;

**2) Greedy Algorithm**

A greedy algorithm selects the best option given each situation provided, regardless if the overall outcome is optimal. It is a simple, intuitve algorithm. Its runtime complexity is also pretty reasonable. In order for a greedy algorithm to give you the best outcome overall the problem must have the following 2 properties.

1. Choosing the best option at each phase can lead to an overall optimal solution
2. The optimal solution is made up of an optimal substructure, meaning the optimal solution to a problem is composed of the optimal solutions to every sub-problem.

The best way to show how the greedy algorithm works is actually by giving examples of that show the shortcomings of a greedy algorithm. Here's an example of the greedy algorithm being applied to the knapsack problem:

{% content-ref url="050-algorithm-examples/054-greedy-algorithm-knapsack-problem.md" %}
[054-greedy-algorithm-knapsack-problem.md](050-algorithm-examples/054-greedy-algorithm-knapsack-problem.md)
{% endcontent-ref %}

Take a look at another example where we are applying the greedy algorithm to a single shortest path problem:

{% content-ref url="050-algorithm-examples/055-greedy-algorithm-shortest-path-problem.md" %}
[055-greedy-algorithm-shortest-path-problem.md](050-algorithm-examples/055-greedy-algorithm-shortest-path-problem.md)
{% endcontent-ref %}

**3) Divide and Conquer Algorithm**

A divide and conquer algorithm breaks a problem up in to smaller parts, solves each part independently, and then merges all of the solutions in to one answer. A merge sort is a good example of a divide and conquer algorithm:

{% content-ref url="050-algorithm-examples/056-merge-sort-example.md" %}
[056-merge-sort-example.md](050-algorithm-examples/056-merge-sort-example.md)
{% endcontent-ref %}

**4) Dynamic Programming Algorithm**

**— TODO**

**5) Backtracking Algorithm**

The backtracking algorithm allows the algorithm to back out when when an invalid state is reached. Take the following example:

{% content-ref url="050-algorithm-examples/057-backtracking-algorithm-example.md" %}
[057-backtracking-algorithm-example.md](050-algorithm-examples/057-backtracking-algorithm-example.md)
{% endcontent-ref %}

**6) Recursive Algorithm**

**— TODO**

**7) Searching Algorithm**

**— TODO**

**8) Sorting Algorithm**

**— TODO**

**9) Hashing Algorithm**

**— TODO**

**10) Machine Learning Algorithm**

**— TODO**



How do you analyze an algorithm?

1. Verify correctness. Does it actually produce the expected output for the given input?
2. Analyze Space Complexity - measures how much extra memory or storage an algorithm needs as its input increases. — TODO: link analysis for space complexity
3. Analyze Time Complexity - how long an agolrithm takes to run compared to the size of the input. Typically measured in Big O Notation. — TODO: link big o notation





