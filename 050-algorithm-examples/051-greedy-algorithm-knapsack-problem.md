# 051 Greedy Algorithm (Knapsack Problem)

In order to show you how a greedy algorithm works, let's show 2 examples where a greedy algorithm wouldn't work.

The goal of the knapsack problem is to get the most value from the items, while minimizing the weight. Let's implement a greedy algorithm that only checks value to keep 2 out of the three values.

Item 1 has a weight of 2 and a value of 6

Item 2 has a weight of 2 and a value of 3

Item 4 has a weight of 4 and a value of 5

The greedy algorithm selects item 1 and item 4. This is a total value of 11, with a total weight of 8. 11/8=1.375. What if you chose item 1 and item 2? 9/4=2.25. The greedy algorithm did not get the optimal solution.&#x20;
