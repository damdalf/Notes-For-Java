# 228 Notes: **WEEK 8** - Monday

## **LIST INTERFACE:**
***

#### **NOTE FOR HW2:**

if a method is private you can change it around - (removed or edited at will)

getPoints(); // allows you extract the sorted points 

***

Collection vs. List vs. Linked List:

1. Collection is a Java interface.

2. List extends Collection by adding more methods.

3. List is a data structure that is 60 years old. Maybe would be nice to call List IndexedCollection or SortedCollection? But we can't.

***
List's additional features as compared to a Collection.

1. **index items - behaves like an array, but fancier**

* void add (int k, E item) - add e item at index k.

* E get(int k) - return item E at index k.

* E set (int k) - set the value of E item at index k.
***

2. **More sophisiticaed iterator that can start at any index.**


* listIterator(); - starts at the beginning like Collection's iterator.

* listItertor(int pos); - starts at index pos, having random access to any index.
***
3. **Methods of List's Iterator:**
* nextIndex() - returns index of the element after the cursor. If at the end of the List, returns size.
* previousIndex() - returns index of the element before the cursor. If at the beginning of the List, returns -1.
* bolean hasNext() - returns true if nextIndex() < size.
* boolean hasPrevious() - returns true if previousIndex() > 0.
* E next() - returns element after the cursor and moves the cursor forward one element.
* E previous() - returns element before the cursor and moves the cursor backwards one element.
* void remove() - removes the last element returned by next() or previous().
    * Can only be called *once* after next() or previous() has been called without ListIterator.add() having been called in between.
* void add(E item) - inserts passed item E immediately before the element that would be returned by next(), and after the element that would be returned by previous().
    * Pretty much inserts the item right where the Cursor sits.
    * Also allows for adding to the end of the list w/o throwing an IndexOutOfBoundsException: iter = iterator(list.size());
* void add(int k, E item) - Adds item E at the specified index, and shifts the elements from the given index to the end of the List to the right by an index of one.
* void set(E item) - Replaces the last element returned by next() or previous() 
    * Cannot be used after remove() or add(), needs to follow a next() or previous().
* E get(int k) - Returns the E element at the index k.
---
* Easiest way to remember for set() and remove() what index needs to be processed is: process last-served element.

	* Cursor behaves like a word processor by sitting between characters.

	* Initially:		|ABCDE
	* iter.next():		A|BCDE

	* Unlike remove() and set(), add() does NOT depends on iteration direction; always adds to the left of the cursor. 