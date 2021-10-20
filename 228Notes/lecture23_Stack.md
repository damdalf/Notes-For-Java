# 228 Notes: **WEEK 9** - Wednesday

## **Stacks And ArrayList vs. LinkedList:**
***

### **How Do ArrayList and LinkedList Compare?**
#### Big O:

* get(int index)

    * ArrayList = O(1)
    * LinkedList = O(n) - LinkedLists are not indexed
* contains(E item)

    * ArrayList = O(n)
    * LinkedList = O(n)
    > Both require sequential search of the array.
* size()

    * ArrayList = O(1)
    * LinkedList = O(1)
    > Size is kept as a variable inside of both lists so we only need to access this variable.
* add(int index)

    * ArrayList = O(n) - we have to shift over all of the other right-hand elements which requires traversing through the entire right side of the list. 
    * LinkedList = O(n) - at again, we cannot access an element at a specific index because LinkedLists do not use indexes.
* remove(E item)

    * ArrayList = O(n) - we have to seach through the entire list to find E item.
    * LinkedList = O(n) - must also traverse through the LinkedList.
* iterator.add()

    * ArrayList = O(n) - add to the index and shift everything to the right.
    * LinkedList = O(1) - we only have to move the pointers from the surrounding nodes, and then increase the size of the LinkedList by one.
* iterator.remove()

    * ArrayList = O(n) - remove from the index and shift everything to the left.
    * LinkedList = O(1) - we only have to move the pointers of the surrounding nodes to point to each other, and decrease the size of the LinkedList by one. 
* iterator.set()

    * ArrayList = O(1) 
    * LinkedList = O(1)
    > In both cases we are only changing the value of an element, we are changing the structure or organization of either data structure. 

* Add k items => Batch-add();

    * ArrayList = O(n * k) - have to insert k items; and if they are the first k indices, each insertion requires approximately n shifts to the right of right-side elements -  have to make a gap for inserted elements.
    * LinkedList = O(n + k) - k insertions; each adjusts up to four references between nodes, and can all be performed in a single pass (iteration over the list which takes O(n)).

* Competitive advantage of ArrayList is instant random access. 
* Competitive advantage of LinkedList is instant adds and deletes. 

***

### **Stack**
***

Stacks consist of the following methods - think of it like a like a stack of cards:
> Last-in, first-out.

* push(E data) - adds the data to the top of the stack.
* pop(E data) - removes the data element at the top of the stack. 
* peek()
* isEmpty()
* size()

### **Stack Applications**
***

Java and most other languages call stacks crash if it fills 1 - 2 MBs with method call history (all suspened methods).

It crashes because in non-recursive software, the stack depth would never exceed 70 nested methods deep. 

98% chance it's a wrong terminating recursion.
2% chance it is a good recursion that needs more space. Need to restart Java with a parameter increasing the memory available to the call stack.

