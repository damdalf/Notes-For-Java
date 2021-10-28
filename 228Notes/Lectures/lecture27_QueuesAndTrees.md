# 228 Notes: **WEEK 10** - Wednesday

## **Lecture 27 - Queues and Trees:**
 - QuickSort -> Queues will appear on the exam
(lecture 27 because we are studying out of lecture 27.pdf, georgi's math confuses me but it's okay)
***
## **Queues**
* Queue - only has access at the front and rear of the queue
    * first in first out ADT
    * Queue extends Collection 
    * LinkedList extends Queue
* Java provides Deque, which can act as a Queue
* Java provides LinkedList which can also act as a Queue

So Queue behaves like a Collection, not like a list. It's a bag, you cannot move backwards, and there is no random access. Can only go forward. 

ArrayList - delete, cursor
DLL - cursor, pending
ListIterator - bidirectional

The Java implementation of Queue has two kinds of each method; one that throws an exception and ones that do not.

***
Linked-List Implementation with Nodes:

1. Singly-linked list with head and tail pointers is enough for a Queue implmentation. Remove at head, add at tail. This could be a doubly-linked list, but that just creates more references for us to change. May or may not have dummy nodes.

    1a. We can implement Queue as a circular-linked list with ONLY a tail pointer, and no head pointer. Then we remove from tail -> next and add at tail or tail -> previous.

2. Array implementation will need two index variables: first and last, which both equal 0 at the beginning. We add elements at the last index, and increment last. We remove elements at the first index, and increment first.

    2a. Solutions to Running out of Index Space

    * copy current array over into a new array
        * not particularly wasteful because the old array is nearly empty.
    * Reset the first and last indices somehow so we can re-utilize existing empty array.
        * we can do it with an if statement
        * most elegant way is to use modular arithmetic to roll over the indices to the starting index of 0

        instead of last++; first++;

        we now write:

        last = (last + 1) % arr.length;

        first = (first + 1) % arr.length;

        This turns a linear array in memory to a circular array where we no longer care about the individual indices.

        Note: With this arithmetic, when last = first, the array could either be empty or full. 

        But, we can't tell what the array state is by looking at the indices. Thus, if we add a rule that the last should always be an empty index, then when last == first we know that the queue is empty. 

        We can implement this with an extra check when advancing last:

        ```java
        if((last + 1) % arr.length == first)
        {
            return IllegalStateException;
        }
        ```
        >The above code would be found in add()

        At a full queue, we still have one empty element. 

        The above discussion assumed that we cannot grow the queue; but we can! 

        We can use our old CheckCapacity() method and double the array when we run out of space. 

        1. One way to fill the new array is to dequeue everything from the old array and enqueue it in the new array.

        2. For profiling purposes and the most efficient code, we can use Array.copy() which SHOULD do a direct memory copy. 
            * can also use Array.copy(int i, int j) to copy elements from a particular range of indices. 

Final note: Java's LinkedList implements queue methods, so you don't have to write your own.

***

## **Trees**
* tree - a connected graph without a cycle.
    * graphs are made of vertices and edges. Vertices carry payloads.
        * edges connect vertexes to each other.
        * the root is the ancestor to every one

    * We create trees by taking Linked-List nodes and adding links to as many nodes as we need.
    * Removing one edge disconnects the tree.
    * Adding one edge creates a cycle and the trees become a graph. 
    * Nodes are the endpoints of a tree so there is one extra node compared to the number of edges.
    * We make a rooted tree by promoting an arbitrary node of a tree to be the root.
        * All other nodes are now considered its descendants.

