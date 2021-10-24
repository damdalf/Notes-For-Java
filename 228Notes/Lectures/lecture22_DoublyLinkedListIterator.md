# 228 Notes: **WEEK 8** - Friday

## **Doubly-Linked List Iterator:**
***

### **For Homework 2:**

```java
@Override
public int compare(Point a, Point b)
{
    return a.compareTo(b);
}
```

This prevents having duplicate code in different methods and potentially deadly bugs when two pathways through the code yield different results, because one of them was not edited at some unspecifiied time in the past.

Private methods are free game; these are hidden from the client. 

compareTo() wraps around compare() in HW2.
***

Unlike doubly-linked collection, add() without an iterator adds behind the tail to add the element(s) in order. In DL collection we added to the head, but this means that the last itema dded would be the first item in the sequence, which happened to be irrelevant in collection because it does not keep tracking of ordering. 

* Doubly-linked list iterator is an asynchronus iterator. 

>int index is the "array" index of the cursor

>int direction is the BEHIND or AHEAD, used only for set() and remove().

>We do not have a "pending" reference, but we COULD write the iterator with one.

The reason that we try so many different iterators is to exercise our understanding of linked lists, so that when we get that question during an interview about data structures we ace it.

* direction: BEHIND, AHEAD, NONE
    * TO_THE_LEFT, TO_THE_RIGHT
    > -1 TO THE LEFT, +1 TO THE RIGHT for actual integer values for int direction.

Asymmetry: going forward the cursor is placed on the node BEYOND the last served node. BUT, going backwards results in the cursor being placed on the last served node. 

1. Method code:

```java
nextIndex()
//index is where the next element should come from, asymmetric because private index means "where the cursor is" while public index means "where the next node is".
{
    return index;
}

previousIndex()
// cursor rests on the current node after a previous.
{
    return index - 1;
}

hasNext()
// translated: we are at a node before the tail, because tail is at the index size(). 
{
    return index < size;
}

hasPrevious()
// translated: is there a node between myself and the head? The asymmetry prevents us from never having the cursor sit on the head.
{
    return index > 0;
}

```

The following are all iterator-invoked methods:
```java
public E next()
// advance through the list and serve next available item. Throw exception if we are the end of the sequence. Change the index, and change the direction to BEHIND == TO_THE_LEFT.
{
    if(!hasNext())
    {
        throw new NoSuchElementException();
    }

    E returnVal = cursor;
    cursor = cursor.next().data;
    index++;
    direction = BEHIND;

    return returnVal;
}

public E previous()
// worry about asymmetry. Retreat through the list and serve the previous item, if available. Otherwise, throw exception. Decrement index, set direction to AHEAD == TO_THE_RIGHT.
{
    if(!hasPrevious())
    {
        throw new NoSuchElementException();
    }

    cursor = cursor.previous();
    index--;
    direction = AHEAD;

    return cursor.data;
}

public boolean add(E item)
// add to the left of the cursor regardless of direction. Works at the tail, and the first node after the head dummy. Adding to the left is always correct. Increment size, increment index, reset direction. 
{
    Node newNode = new Node(item);
    link(current.previous, newNode);
    size++;
    index++;
    direction = NONE;

    return true;

}

public boolean set(E item)
// perform a replace on the last served element. Throw exception if nothing was served. Return the last served element that got replaced by the current arguement. set() can be performed consecutively, no need for resetting or changing direction.
{
    if(direction == NONE)
    {
        throw new IllegalStateException();
    }

    E returnVal = null;

    if(direction == AHEAD) //previously performed previous().
    {
        E returnVal = cursor.data;
        cursor.data = item;
    }
    else if(direction == BEHIND) //previously performed next();
    {
        E returnVal = cursor.previous.data;
        cursor.previous.data = item;
    }

    return returnVal;
}
```
