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

### Binary Space Partitioning

Binary space partitioning is a way of breaking up a 2d space in to smaller and smaller halves in order to quickly traverse the 2d space and determine what objects are in that sub region. For example, let's say we broke up a space like this:

```
Initial 2D Space:
┌─────────────────────────────────────┐
│                                     │
│                                     │
│                                     │
│                                     │
│                                     │
│                                     │
│                                     │
│                                     │
└─────────────────────────────────────┘

Split 1 (Vertical):
┌─────────────────┬───────────────────┐
│       A         │         B         │
│                 │                   │
│                 │                   │
│                 │                   │
│                 │                   │
│                 │                   │
│                 │                   │
│                 │                   │
└─────────────────┴───────────────────┘

Split 2 (Horizontal on A - splits A in half):
┌─────────────────┬───────────────────┐
│       A1        │         B         │
│                 │                   │
│                 │                   │
│                 │                   │
├─────────────────┤                   │
│       A2        │                   │
│                 │                   │
│                 │                   │
│                 │                   │
└─────────────────┴───────────────────┘

Split 3 (Vertical on B - splits B in half):
┌─────────────────┬─────────┬─────────┐
│       A1        │   B1    │   B2    │
│                 │         │         │
│                 │         │         │
│                 │         │         │
├─────────────────┤         │         │
│       A2        │         │         │
│                 │         │         │
│                 │         │         │
│                 │         │         │
└─────────────────┴─────────┴─────────┘

Split 4 (Horizontal on A2 - splits A2 in half):
┌─────────────────┬─────────┬─────────┐
│       A1        │   B1    │   B2    │
│                 │         │         │
│                 │         │         │
│                 │         │         │
├─────────────────┤         │         │
│      A2.1       │         │         │
├─────────────────┤         │         │
│      A2.2       │         │         │
│                 │         │         │
└─────────────────┴─────────┴─────────┘
```

The corresponding binary tree for representing this space would look like this:

```
                   Root
                     |
         ┌───────────┼───────────┐
         |                       |
         A                       B
         |                       |
     ┌───┼───┐               ┌───┼───┐
     |       |               |       |
    A1      A2              B1      B2
             |
         ┌───┼───┐
         |       |
       A2.1    A2.2
```

### File Systems

File systems are based on trees, however not binary trees. Here's a simple example of what the tree structure of a file system would look like.

```
/
├── home/
│   ├── bob/
│   │   ├── Documents/
│   │   │   ├── my_deepest_secrets.txt
│   │   │   ├── why_pineapple_pizza_is_good.doc
│   │   │   └── passwords_definitely_not_here.txt
│   │   ├── Downloads/
│   │   │   ├── totally_not_a_virus.exe
│   │   │   ├── cat_memes_volume_47.zip
│   │   │   └── definitely_homework.pdf
│   │   ├── Music/
│   │   │   ├── baby_shark_10_hour_loop.mp3
│   │   │   └── screaming_goats_remix.wav
│   │   └── Pictures/
│   │       ├── blurry_sunset_attempt_34.jpg
│   │       ├── my_left_toe.png
│   │       └── sandwich_i_made_yesterday.gif
│   └── alice/
│       ├── bin/
│       │   ├── make_coffee.sh
│       │   ├── procrastinate.py
│       │   └── blame_the_intern.exe
│       └── work/
│           ├── actual_work_folder/
│           │   └── nothing_to_see_here.txt
│           ├── fake_work_folder/
│           │   ├── very_important_spreadsheet.xlsx
│           │   ├── meeting_notes_i_never_read.docx
│           │   └── budget_that_makes_no_sense.pdf
│           └── memes/
│               ├── distracted_boyfriend.jpg
│               ├── this_is_fine.gif
│               └── drake_pointing.png
├── usr/
│   ├── bin/
│   │   ├── sudo_make_me_a_sandwich
│   │   ├── whereis_my_mind
│   │   └── finger_guns
│   └── lib/
│       ├── libconfused.so
│       ├── libsarcasm.so.2
│       └── libprocrastination.a
├── etc/
│   ├── passwd_but_worse
│   ├── hosts_and_ghosts
│   ├── fstab_but_unstable
│   └── crontab_of_doom
├── var/
│   ├── log/
│   │   ├── everything_is_fine.log
│   │   ├── suspicious_activity.log
│   │   └── cats_walking_on_keyboard.log
│   └── spool/
│       ├── mail_from_my_ex/
│       └── printer_that_never_works/
└── tmp/
    ├── temp_file_from_1987.tmp
    ├── cache_of_regrets.cache
    ├── random_binary_blob.bin
    └── file_i_forgot_about.old
```

Just uh, idk tilt your head or turn your screen sideways so it looks like a tree. See it? Sweet.

