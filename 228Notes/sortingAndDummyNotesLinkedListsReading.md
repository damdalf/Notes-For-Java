# 228 Reading: **WEEK 8** - Wednesday

## **SORTING LINKED LISTS AND DUMMY NODES:**
***
### **DEFINITIONS:**
***
* insertion sort (doubly-linked list) - *Starting with the second list element, each element in the linked list is visited. Each visited element is moved back as needed and inserted into the correct position in the list's sorted portion. The list must be a doubly-linked list, since backward traversal is not possible in a singly-linked list*.
    * *Typical Big-O runtime of O(N^2). Even if the list is already sorted, it would still take the algorithm O(N)*.
* insertion sort (singly-linked list) - *Since a singly-linked list only supports inserting a node after an existing list node, the ListFindInsertionPosition algorithm searches the list for the insertion position and returns the list node after which the current node should be inserted. If the current node should be inserted at the head, ListFindInsertionPosition return null*.
    * *The worst case runtime is O(N^2), and the best runtime, which occurs when the list is sorted in descending order, is O(N)*.
* dummy head node - *also known as a header node, a dummy node is a node with an unused data member that always resides at the head of the list and cannot be removed. Using a dummy node simplfies the algorithms for a linked list because the head and tail pointers are never null*.
![](https://i.gyazo.com/c4b61b92cf2ad66450bf283643eb644e.png)
* dummy tail node - *A doubly-linked list implementation can also use 2 dummy nodes: one at the head and the other at the tail. Doing so removes additional conditionals and further simplifies the implementation of most methods*.
![](https://i.gyazo.com/f5f449fd0183f1f635c9e24ec0d9f1f5.png)

### **CODE AND CONCEPTS:**
***
#### **insertionSort for Doubly-Linked Lists**
```Java
ListInsertionSortDoublyLinked(list) {
   curNode = list⇢head⇢next
   while (curNode != null) {
      nextNode = curNode⇢next
      searchNode = curNode⇢prev
      while (searchNode != null and searchNode⇢data > curNode⇢data) {
         searchNode = searchNode⇢prev
      }
      // Remove and re-insert curNode
      ListRemove(list, curNode)
      if (searchNode == null) {
         curNode⇢prev = null
         ListPrepend(list, curNode)
      }
      else {
         ListInsertAfter(list, searchNode, curNode)
      }
      // Advance to next node
      curNode = nextNode
   }
}
```

#### **insertionSort for Singly-Linked Lists**
```Java
ListInsertionSortSinglyLinked(list) {
   beforeCurrent = list⇢head
   curNode = list⇢head⇢next
   while (curNode != null) {
      next = curNode⇢next
      position = ListFindInsertionPosition(list, curNode⇢data)

      if (position == beforeCurrent)
         beforeCurrent = curNode
      else {
         ListRemoveAfter(list, beforeCurrent)
         if (position == null)
            ListPrepend(list, curNode)
         else
            ListInsertAfter(list, position, curNode)
      }

      curNode = next
   }
}

```

#### **Since Linked_Lists do not allow indexed access of elements, there are certain sorting algorithms that do not sort Linked_Lists efficiently:**
![](https://i.gyazo.com/7ddf4d6dae6cf13bcbc3871974ddb04d.png)