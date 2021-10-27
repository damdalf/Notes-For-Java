# 228 Reading: **WEEK 10** - Wednesday

## **Queues and Deques:**
***
### **DEFINITIONS:**
* queue - *a queue is an ADT in which items are inserted at the end of the queue and removed from the front of the queue*.
    *  A queue is known as a first-in, first-out ADT.
* deque - *a deque is an ADT in which items can be inserted and removed at both the front and back*.
***
### **CODE AND CONCEPTS FOR QUEUES:**
![](https://i.gyazo.com/2dbe38979ce983b13898c01e0d357fcc.png)
Furthermore, a queue is often implemented using a linked list, with the list's head node representing the queue's front, and the list's tail node representing the queue's end. Enqueueing an item is performed by creating a new list node, assigning the node's data with the item, and appending the node to the list. Dequeuing is performed by assigning a local variable with the head node's data, removing the head node from the list, and returning the local variable. 
![](https://i.gyazo.com/841da882f299b25d07d0637ec5dcb188.png)
***
### **CODE AND CONCEPTS FOR DEQUES:**
![](https://i.gyazo.com/57d45e407c0674ff51627c44c2c0d08f.png)