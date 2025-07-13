# 001 Lists

## What is a list?

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

## Linked Lists

Lists are implemented on a linked list as the underlying data structure. This linked lists might use a list data structure, which is a data structure that contains the linked lists head, tail, and length. If the linked list is created without a list data structure you will still have to have at least 2 variables to store the head and the tail of the linked list.

In a singly-linked list each node of the list contains only a pointer to the next node.

Searching a linked list happens by checking the current node, and if it is not the desired search value then moving on to the next node. It will continue this until the desired value is found and returned.

A doubly-linked list is another data structure that can be used to implement an abstract data type list. In a doubly-linked list each node has a pointer to both the next node and the previous node.

A circular linked list is a list where the tail node points back to the head node instead of pointing to null.

A traversal algorithm visits all nodes in a list and preforms an opteration on each node. In a circularly linked list the traversal must stop once the head has been pointed at twice, as opposed to when the tail node points at null.

Both merge sorts and insertion sorts can be adapted to work on linked lists, however they are harder to implement on singly-linked lists.

Sometimes a linked-list will contain a dummy node, which is a node with a null value, so that the pointers for head and tail always point at a node, instead of pointing a null they point at the dummy node. The head pointer always points at the dummy node, and the tail pointer will point at the dummy node if there are no nodes in the linked list.

Recursion is a good way to traverse a linked list forward or backwards. Traversing a linked list forward is simple, perform the action of the function before calling the function again

```
recursiveFunction(node):
    if (node != null):
        performAnAction(node)
        recursiveFunction(nextNode)
    return
```

It's also simple to traverse a linked list in reverse with recursion, simply call the recursive method before the action of the function. This way the action is performed on each node starting with the tail instead.

```
recursiveFunction(node):
   if (node != null):
      recursiveFunction(nextNode)
      performAnAction(node)
   return
```

## Array Based Lists

An array based list is simple the an abstract data type list built on an array as the underlying data structure. Sorts and searches work better on arrays than on linked lists, however insertions work better on linked lists as they do not have to resize like an array.

Most underlying arrays must be of a fixed size, although the abstract data type list may dynamically resize the array for you. Typically the array will be allocated to a fixed size, it must be at least 1, and each time it has to resize it will resize at double the current array length. Resize operations happen with a runtime complexity of O(n).

