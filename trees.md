# Trees

## Binary Trees

A binary tree is a simple data structure where each node can have 0, 1, or 2 children. If it has children they are differentiated between left child and right child. If a node has no parent node it is the root node, there can only be one node with no parent. If a node has 0 children it is referred to as a leaf node. If it does have children it is referred to as an internal node. The parent nodes of a nodes parent node are referred to as ancestors. Take a look at this binary tree:

```
       A
      / \
     B   C
          \
           D
          / \
         E   F
```

* A is the root node
* B is a leaf node, and the left child node of node A
* C is an internal node, and the right child node of node A
* D is also an internal node, C is the parent node of D, and A is node D's ancestor
* E and F are also leaf nodes, and are D's left and right children respectively

### More Terminology

* The link between two nodes is called an edge. The edges are highlighted below:

<pre><code>       A
<strong>      / \
</strong>     B   C
<strong>          \
</strong>           D
<strong>          / \
</strong>         E   F
</code></pre>

* The depth of a node is is how many steps away from the root node it is. Depths are labeled here:

<pre><code><strong>       A          0
</strong>      / \   
<strong>     B   C        1
</strong>          \
<strong>           D      2
</strong>          / \
<strong>         E   F    3  
</strong></code></pre>

* Nodes at the same height form a tree level
* A tree's height is simply the the same as the largest depth. The example tree has a height of 3.

### Types of Binary Trees

A binary tree is considered "full" if every node contains 0 or 2 children. Our example tree is not full, as node C only has one child. If we edited our example tree to be full it would look like this:

```
       A
      / \
     B   C
        / \
       D   E
          / \
         F   G
```

A binary tree is considered "complete" if all levels, with an exception to the last level, contain all possible nodes and all nodes are as far left as they can be. Our example tree was not complete, this is what it would look like if it was complete:

```
       A
      / \
     B   C
    / \ / 
   D  E F
```

A binary tree is considered perfect if all internal nodes have 2 children, and all leaf nodes are on the same level. Our example tree is not perfect, this is what it would look like if it was perfect:

```
      A
     / \
    B   C
   / \ / \
  D  E F  G
```

Here are some more examples of trees and their classifications:

```
                    A                          🚫Full
                    |                          🚫Complete
          ┌─────────────────────┐              🚫Perfect
          |                     |
          B                     C
          |                     |
      ┌───────┐             ┌──────┐
      |       |             |      |
      D       E             F      G
      |       |             |       
    ┌────┐  ┌────┐          |       
    |    |  |    |          |       
    H    I  J    K          L
```

```
                    A                          🚫Full
                    |                          🚫Complete
          ┌─────────────────────┐              🚫Perfect
          |                     |
          B                     C
          |                     |
      ┌───────┐             ┌───
      |       |             |      
      D       E             F      
      |       |             |       
    ┌────┐  ┌────┐        ┌────┐       
    |    |  |    |        |    |   
    G    H  I    J        J    K
```

```
                    A                          ✅Full
                    |                          🚫Complete
          ┌─────────────────────┐              🚫Perfect
          |                     |
          B                     C
          |                     |
      ┌───────┐             ┌───────┐
      |       |             |       |
      D       E             F       G
              |                     |
            ┌────┐                ┌────┐   
            |    |                |    |
            H    I                L    M    
```

```
                    A                          🚫Full
                    |                          🚫Complete
          ┌─────────────────────┐              🚫Perfect
          |                     |
          B                     C
          |                     |
      ┌───                       ────┐
      |                              |
      D                              E
      |                              |
    ┌────┐                         ┌────┐   
    |    |                         |    |
    F    G                         H    I    
```

```
                    A                          ✅Full
                    |                          ✅Complete
          ┌─────────────────────┐              🚫Perfect
          |                     |
          B                     C
          |                     |
      ┌───────┐             ┌───────┐
      |       |             |       |
      D       E             F       G
      |       |             |       
    ┌────┐  ┌────┐        ┌────┐       
    |    |  |    |        |    |   
    H    I  J    K        L    M
```

```
                    A                          ✅Full
                    |                          ✅Complete
          ┌─────────────────────┐              ✅Perfect
          |                     |
          B                     C
          |                     |
      ┌───────┐             ┌───────┐
      |       |             |       |
      D       E             F       G
      |       |             |       |
    ┌────┐  ┌────┐        ┌────┐  ┌────┐   
    |    |  |    |        |    |  |    |
    H    I  J    K        L    M  N    O    
```

