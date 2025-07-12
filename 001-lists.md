# 001 Lists

We touched on lists in the introduction. A list is an abstract data type that is... a list of values. Duplicates are allowed, and it is unordered.

What are some common operations that an abstract data type list could have?

Starting with the list \[33,55,22] here are some operations a list could have

| Operation               | Result         |
| ----------------------- | -------------- |
| list.Append(44)         | \[33,55,22,44] |
| list.Prepend(44)        | \[44,33,55,22] |
| list.insertAfter(33,44) | \[33,44,55,22] |
| list.Remove(55)         | \[33,22]       |
| list.Search(22)         | 22             |
| list.Search(44)         | null           |
| list.Print()            | "33 55 22"     |
| list.Reverse()          | \[22,55,33]    |
| list.Sort()             | \[22,33,44]    |
| list.IsEmpty()          | false          |
| list.Length()           | 3              |

Lists are implemented on a linked list as the underlying data structure. This linked lists might use a list data structure, which is a data structure that contains the linked lists head, tail, and length. If the linked list is created without a list data structure you will still have to have at least 2 variables to store the head and the tail of the linked list.

In a singly-linked list each node of the list contains only a pointer to the next node.

Searching a linked list happens by checking the current node, and if it is not the desired search value then moving on to the next node. It will continue this until the desired value is found and returned.

A doubly-linked list is another data structure that can be used to implement an abstract data type list. In a doubly-linked list each node has a pointer to both the next node and the previous node.

A circular linked list is a list where the tail node points back to the head node instead of pointing to null.

A traversal algorithm visits all nodes in a list and preforms an opteration on each node. In a circularly linked list the traversal must stop once the head has been pointed at twice, as opposed to when the tail node points at null.

