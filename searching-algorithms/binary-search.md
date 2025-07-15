# Binary Search

Binary trees are paticularly useful for searching. A Binary Search Tree is an ordered tree where and nodes left children are less than or equal to the parent node, and it's right children are greater than or equal to the parent node.&#x20;

Like this:

```
                    8                          
                    |                          
          ┌─────────────────────┐              
          |                     |
          4                     12
          |                     |
      ┌───────┐             ┌───────┐
      |       |             |       |
      2       6             10      14
      |       |             |       |
    ┌────┐  ┌────┐        ┌────┐  ┌────┐   
    |    |  |    |        |    |  |    |
    1    3  5    7        9    11 13   15    
```

Binary search trees are so great because at worst your search is O(D+1) where D is the depth of the binary tree. Each node you visit if the value you're searching for is greater than the current node, go right. If it's less than the current node, go left. If you were searching for 11 your algorithm would:

* Starting at node 8 see that 11>8, go right to node 12
* At node 12 see that 11<12, go left to node 10
* At node 10 see that 11>10, go right to node 11
* At node 11 see that 11=11, return the node

If you used an iterative search on a list with the same data you'd have to search 11 out of the 15 values, instead you only searched 4.

Also, look how simple it is in python:

```python
def search(root, key):
    if root is None:
        return null
        
    if root.key == key:
        return root
        
    if root.key < key:
        return search(root.right, key)
    
    return search(root.left, key)
```
