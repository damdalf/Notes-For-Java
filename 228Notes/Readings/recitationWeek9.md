# 228 Recitation: **WEEK 9** - Wednesday

## **Iterators and Collections:**
***
## Iterators
* An iterator is an object that sllows you to traverse through a collection.
* Why do we use an iterator?
     * To more efficiently traverse, add, remove, and replace collection elements.
    
Iterators are useful for ArrayLists. 
![](https://i.gyazo.com/9c432e8878b2dac5783bb8e39efd41c6.png)

remove() and set() cannot be called consecutively, with or without each other. Both functions can only be called after traversing an element, which means you have either used next() or previous().

ListIterator is a subtype of Iterator. 
![](https://i.gyazo.com/f87e9549342a4fb1099874d7d1d4a169.png)

In either case, the Iterator sits in bewteen elements like a text cursor. 

* Removing elements using an iterator never truly 'deletes' the element. It merely 'forgets' about this element by assigning the next elements's 'previous' pointer to the element before the one being removed. It then assigns the previous element's 'next' pointer to the element folling the one to be removed.

In any case, adding and removing an element in a linked-list is all done by creating or removing connections between the elements.

Wait, hold up, what's the difference between an ArrayList and a LinkedList?
![](https://i.gyazo.com/516e84fa4e3994e5f1c9bb38ce638882.png)

