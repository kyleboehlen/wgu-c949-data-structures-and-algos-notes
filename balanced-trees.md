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

### Red Black Trees

## Rotations



