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

This is called the knapsack problem. The goal is to get the most value from the items, while minimizing the weight. Let's implement a greedy algorithm that only checks value to keep 2 out of the three values.

Item 1 has a weight of 2 and a value of 6

Item 2 has a weight of 2 and a value of 3

Item 4 has a weight of 4 and a value of 5

The greedy algorithm selects item 1 and item 4. This is a total value of 11, with a total weight of 8. 11/8=1.375. What if you chose item 1 and item 2? 9/4=2.25. The greedy algorithm did not get the optimal solution.&#x20;

Take a look at another example where we are applying the greedy algorithm to a single shortest path problem, where we are starting at position A and trying to get to the End

```
        A
       / \
      2   1
     /     \
    B       C
    |       |
    2       4
     \     /
       END
```

You'll see that the greedy algorithm will choose to go to location C first because it is the shortest path, and end up with a total of 5. The optimal path would have been to go through location B for a total of 4.

**3) Divide and Conquer Algorithm**

A divide and conquer algorithm breaks a problem up in to smaller parts, solves each part independently, and then merges all of the solutions in to one answer. A merge sort is a good example of a divide and conquer algorithm. How does a merge sort work?

Take an array:

```
Original: [64, 34, 25, 12, 22, 11, 90]
```

First it splits the orignal array in half over and over again until each node only consists of 1 element.

```
[64, 34, 25, 12, 22, 11, 90]            1 node
       /              \             
[64, 34, 25]      [12, 22, 11, 90]      2 nodes
    /    \           /         \
[64]   [34, 25]   [12, 22]   [11, 90]   4 nodes
  |     /    \     /    \     /    \
[64] [34]   [25] [12]  [22] [11]  [90]  7 nodes 
```

It then merges each of the nodes in the reverse order. Look at how many nodes are created in each step of the divde phase above. In the conquer phase we're going to combine nodes instead of splitting them by comparing the first items of each node and putting whichever one is smaller first in the merged node. On the first round this is very simple because we're only comparing one value to one value in each node. Take a look at the result:

```
[64] [25,34] [12,22] [11,90]   4 nodes 
```

We have 4 nodes, in each of the nodes all of the values are in order. Lets take a closer look at how we would merge these nodes in the next step. First we would create 2 nodes for the previous 4 nodes to merge in to:

```
[64] [25,34] [12,22] [11,90]   4 nodes
[          ] [             ]   2 nodes     
```

Then we start by comparing only the first values of each node to each other. The first values in the left most nodes are 64 and 25. 25 is less than 64 so it gets added to the new node first:

```
[64] [34] [12,22] [11,90]   4 nodes
[   25  ] [             ]   2 nodes     
```

Now the first most values in each of the left most nodes is 64 and 34. 34 is less than 64 so it gets added to the new node next:

```
[64] [  ] [12,22] [11,90]   4 nodes
[ 25,34 ] [             ]   2 nodes     
```

Lastly only 64 is left, so it gets added to the new node next:

```
[  ]  [  ] [12,22] [11,90]   4 nodes
[25,34,64] [             ]   2 nodes 
```

Let's quickly show how that would look for the right most nodes. It'll happen in 4 steps:

1. ```
   [  ]  [  ]  [22] [11,90]    4 nodes
   [25,34,64]  [   12     ]    2 nodes
   ```
2. ```
   [  ]  [  ]  [12,22] [90]    4 nodes
   [25,34,64]  [     11   ]    2 nodes
   ```
3. ```
   [  ]  [  ]     [22] [90]    4 nodes
   [25,34,64]     [ 11,12 ]    2 nodes
   ```
4. ```
   [  ]  [  ]    [  ]  [90]    4 nodes
   [25,34,64]    [11,12,22]    2 nodes
   ```
5. ```
   [  ]  [  ] [  ]     [  ]    4 nodes
   [25,34,64] [11,12,22,90]    2 nodes
   ```

The end result will be a sorted list of the same array:

6. ```
   [11,12,22,25,34,64,90]      1 node
   ```

The time complexity for a merge sort is O(n log(n)) which is considered good I guess, I don't even know what that means yet. Here's an example of merge sort in Python tho:

```
def mergeSort(arr):
  if len(arr) <= 1:
    return arr

  mid = len(arr) // 2
  leftHalf = arr[:mid]
  rightHalf = arr[mid:]

  sortedLeft = mergeSort(leftHalf)
  sortedRight = mergeSort(rightHalf)

  return merge(sortedLeft, sortedRight)

def merge(left, right):
  result = []
  i = j = 0

  while i < len(left) and j < len(right):
    if left[i] < right[j]:
      result.append(left[i])
      i += 1
    else:
      result.append(right[j])
      j += 1

  result.extend(left[i:])
  result.extend(right[j:])

  return result

mylist = [3, 7, 6, -10, 15, 23.5, 55, -13]
mysortedlist = mergeSort(mylist)
print("Sorted array:", mysortedlist) 
```



**4) Dynamic Programming Algorithm**

**5) Backtracking Algorithm**

The backtracking algorithm allows the algorithm to back out when when an invalid state is reached. Take the following example:

<pre><code>XYZ BACKTRACKING SEARCH TREE
Goal: find all of the ways to fill 3 indexes in an array with the following constraints:
Constraint 1: The only values that can be used are X, Y, and Z
Constraint 2: Z cannot be adjacent to X
Constraint 3: The array cannot contain 2 indexes of the same value
Positions: [0] [1] [2]

                                ROOT
                                 |
        ┌────────────────────────┼────────────────────────┐
        |                        |                        |
<strong>        X                        Y                        Z           pos[0]
</strong>        |                        |                        |
   ┌────┼────┐              ┌────┼────┐              ┌────┼────┐
   |    |    |              |    |    |              |    |    |
   X    Y    Z              X    Y    Z              X    Y    Z      pos[1]   
   |    |    |              |    |    |              |    |    |
   ✗    |    ✗              |    ✗    ✗              ✗    |    ✗
 (dup)  |  (X→Z)            |  (dup) (X→Z)         (Z→X)  |  (dup)
        |                   |                             |    
   ┌────┼────┐         ┌────┼────┐                   ┌────┼────┐
   |    |    |         |    |    |                   |    |    |
   X    Y    Z         X    Y    Z                   X    Y    Z      pos[2]
   |    |    |         |    |    |                   |    |    |
   ✗    ✗    ✓         ✗    ✗    ✗                   ✓    ✗    ✗
 (dup)(dup)(XYZ)     (dup)(dup)(X→Z)               (ZYX)(dup)(dup)
             ↑                                       ↑   
           VALID                                   VALID 
</code></pre>

**6) Recursive Algorithm**

**7) Searching Algorithm**

**8) Sorting Algorithm**

**9) Hashing Algorithm**

**10) Machine Learning Algorithm**



How do you analyze an algorithm?

1. Verify correctness. Does it actually produce the expected output for the given input?
2. Analyze Space Complexity - measures how much extra memory or storage an algorithm needs as its input increases. --TODO: link analysis for space complexity
3. Analyze Time Complexity - how long an agolrithm takes to run compared to the size of the input. Typically measured in Big O Notation. --TODO: link big o notation





