# 228 Reading: **WEEK 8** - Monday

# **LIST INTERFACE:**
***

## **DEFINITIONS:**

* list - *a common ADT for holding ordered data, having operations like append a data item, remove a data item, search whether a data item exists, and print the list*.
* list traversal - *an aglorithm that visits all nodes in the list and performs an operation on each node*.

    *  A common traversal operation prints all list nodes. The algorithm starts by pointing a curNode pointer to the list's head node. While curNode is not null, the algorithm prints the current node, and then points curNode to the next node. After the list's tail node is visited, curNode is pointed to the tail node's next node, which does not exist. So, curNode is null, and the 
    traversal ends.

        * The traversal algorithm supports both singly-linked and doubly-linked lists, since both contain a "next" pointer.
* reverse traversal - *visits all nodes in the list starting from the list's tail node and ending after visiting the list's head node*.

    * This only works on doubly-linked lists.
---
* ascending order, which is sorting done from the smallest value to the largest value, behaves the same way as sorting by alphabetical order.

### **COMMON LIST ADT OPERATIONS:**
![](https://i.gyazo.com/472db34693b48436d0f6dfba9e1532de.png)

### **LIST TRAVERSAL:**
```Java
ListTraverse(list) {
   curNode = list⇢head // Start at head

   while (curNode is not null) { 
      Print curNode's data        
      curNode = curNode⇢next
   }
}
```

### **REVERSE TRAVERSAL:**
```Java
ListTraverseReverse(list) {
   curNode = list⇢tail // Start at tail

   while (curNode is not null) { 
      Print curNode's data        
      curNode = curNode⇢prev
   }
}
```