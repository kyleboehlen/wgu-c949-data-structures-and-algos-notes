# 054 Greedy Algorithm (Shortest Path)

A greedy algorithm is not allowed to back up once it makes a choice. This leads to a faster algorthim, but with the downside of not always finding the most optimal solution.

In order to show you how a greedy algorithm works, let's show 2 examples where a greedy algorithm wouldn't get the most optimal solution.

This is an example of how a greedy algorithm would approach the shortest path problem where we are starting at position A and trying to get to the End. At each point in the journey the algorithm can only solve the problem in front of it. It cannot check if there was a better route and back up once it has new information.

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

You'll see that the greedy algorithm will choose to go to location C first because it is the shortest path, and will end up with a total of 5. The optimal path would have been to go through location B for a total of 4.
