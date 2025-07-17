# Merge Sort

How does a merge sort work?

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

```python
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
