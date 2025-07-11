# 054 Backtracking Algorithm Example

<pre><code>XYZ BACKTRACKING SEARCH TREE
Goal: find all of the ways to fill 3 indexes in an array with the following constraints:
Constraint 1: The only values that can be used are X, Y, and Z
Constraint 2: Z cannot be adjacent to X
Constraint 3: The array cannot contain 2 indexes of the same value
Positions: [0] [1] [2]

<strong>                                ROOT
</strong>                                 |
        ┌────────────────────────┼────────────────────────┐
        |                        |                        |
<strong>        X                        Y                        Z           pos[0]
</strong>        |                        |                        |
   ┌────┼────┐              ┌────┼────┐              ┌────┼────┐
   |    |    |              |    |    |              |    |    |
<strong>   X    Y    Z              X    Y    Z              X    Y    Z      pos[1]   
</strong>   |    |    |              |    |    |              |    |    |
   ✗    |    ✗              |    ✗    ✗              ✗    |    ✗
<strong> (dup)  |  (X→Z)            |  (dup) (X→Z)         (Z→X)  |  (dup)
</strong>        |                   |                             |    
   ┌────┼────┐         ┌────┼────┐                   ┌────┼────┐
   |    |    |         |    |    |                   |    |    |
<strong>   X    Y    Z         X    Y    Z                   X    Y    Z      pos[2]
</strong>   |    |    |         |    |    |                   |    |    |
   ✗    ✗    ✓         ✗    ✗    ✗                   ✓    ✗    ✗
<strong> (dup)(dup)(XYZ)     (dup)(dup)(X→Z)               (ZYX)(dup)(dup)
</strong>             ↑                                       ↑   
           VALID                                   VALID 
</code></pre>

Follow each tree path to see how this algorithm would calculate the valid solutions. You'll see (dup) for when a duplicate value would be in the array (violating constraint 3), (X→Z) or (Z→X) when the solution violates constraint 3, and that the two valid answers (XYZ) and (ZYX).

Because it prunes invalid paths early on it's more effecient than a brute force algorithm. You'll see at position 1 that it ignores 2/3rds of the potential routes.
