# 228 Reading: **WEEK 8** - Wednesday

## **STACKS AND LINKED LISTS:**
***
### **DEFINITIONS:**
***
* stack - *a stack is ADT in which items are only inserted or removed from the top of the stack.*.
    * push - *inserts an items on the top of a stack*.
    * pop - *removes and returns the item at the top of the stack*.
### **CODE AND CONCEPTS:**
***
A stack is referred to as a 'last-in, first-out' ADT, and can be implemented using a linked list, an array, or a vector.

![](https://i.gyazo.com/c5e40c18513d300654e8d74b5e3d6a83.png)

Stacks are often implemented using a linked-list, with the head node being the stack's top.

* A push is performed by creating a new list node, assigning the node with the corresponding data, and then prepending the node to the front / top of the list.

    * Prepending the node is what handles inserting the new node to the top of the stack and assigning its next pointer to the following node.

* A pop is performed by assigning a local variable with the head node's data, removing the head node from the list, and then returning the local variable.

    * Note that the DATA of the head node is returned, not the head node itself.
