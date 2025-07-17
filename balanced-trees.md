# Balanced Trees

## AVL Trees

An AVL tree is a binary search tree that maintains a balanced structure after insertions or deletions in order to ensure that search and other operations stay efficient with the tree. There are two requirements:

1. It needs to be a binary search tree, which means all nodes must be ordered as binary search trees are ordered binary trees.
2. It ensures that given any node the height of the node's left subtree and right subtree will never differ by more than 1.

Let's look at some examples:

```
✅  B
   / \
  A   C
      |
      D
```

This is an AVL.

```
 🚫 B
   / \
  A   C
      |
      E
      |
      D
```

Not an AVL. Look at the root node B. It's left subtree has a height of 1, it's right sub tree has a height of 3.

```
🚫   92
       \
       96
        |
       98
```

Not an AVL.

```
✅    500
     /   \
   400   600
   /      \
  300     700
```

This is an AVL.

```
✅    500
     /   \
   400   600
   /      \
  300     700
  /        \
 200       800
```

Still an AVL.

```
🚫    500
     /   \
   200   888
   /      \
  300     62
```

Not an AVL. It has to be ordered to be a binary search tree, it has to be a binary search tree to be an AVL.

AVL trees are not perfect trees, however they never have a height of more than 1.5x the minimum height.

\--TODO: show a minimum height on a perfect binary tree with 7 nodes, show a valid AVL tree with 7 nodes that has a height of 3 instead of the perfect height of 2

— TODO: Insertions

— TODO: Removals

## Red Black Trees

Rules of a red black tree:

* Red black trees must be valid binary search trees
* Every node is either red or black
* The root node is black
* A red node cannot have red children
* A null child is considered to be a black leaf node
* All paths from any node to any null leaf descendant node must contain the same number of black nodes

— TODO: Insertions, show RB tree rebalance algorithm, maybe just line out steps. Let's try that:

1. Regular binary tree insertion
2. Check if the parent node is null, if so then the inserted node is a root node. Change the parent node to black. You can stop balancing here. If not, continue on.
3. If the parent node is not null, and the parent node is black, no balancing needs to be done. Unlike an AVL tree we do not need to check height. Red black trees only need to make sure that no path is double the length of any other path. AVL trees ensure no height is greater than 1.5 the minimum possible height. You can stop balancing here. If not, continue on.
4. If the parent node is not null, and the parent node is red, then a red black tree rule has been violated.
5. &#x20;If the node has an uncle node and the uncle node is red then set the parent node and the uncle node to black. Set the grandparent node to red. Start this algorithm over starting with the grandparent node. Otherwise, continue on.
6. If the node is the right child, and the nodes parent node is a left child, then rotate left on the parent node. If the node is a left child, and the parent node is a right child, rotate right on the parent node
7. Set the parent node to black
8. Set the grandparent node to red
9. If the node is a left child, rotate right on the grandparent, otherwise rotate left on the grandparent

Here is what that looks like as pseudocode:

```
RBTreeBalance(tree, node) {
   if (node⇢parent == null) {
      node⇢color = black
      return
   }
   if (node⇢parent⇢color == black)
      return
   parent = node⇢parent
   grandparent = RBTreeGetGrandparent(node)
   uncle = RBTreeGetUncle(node)
   if (uncle != null && uncle⇢color == red) {
      parent⇢color = uncle⇢color = black
      grandparent⇢color = red
      RBTreeBalance(tree, grandparent)
      return
   }
   if (node == parent⇢right &&
       parent == grandparent⇢left) {
      RBTreeRotateLeft(tree, parent)
      node = parent
      parent = node⇢parent
   }
   else if (node == parent⇢left &&
            parent == grandparent⇢right) {
      RBTreeRotateRight(tree, parent)
      node = parent
      parent = node⇢parent
   }
   parent⇢color = black
   grandparent⇢color = red
   if (node == parent⇢left)
      RBTreeRotateRight(tree, grandparent)
   else
      RBTreeRotateLeft(tree, grandparent)
}
```

— TODO: Removals

## Rotations

\--TODO: this video seems good: [https://www.youtube.com/watch?app=desktop\&v=vRwi\_UcZGjU\&t=0s\&t=1023](https://www.youtube.com/watch?app=desktop\&v=vRwi_UcZGjU\&t=0s\&t=1023)

