# 228 Notes: **WEEK 8** - Wednesday

## **DOUBLY-LINKED IMPLEMENTATION OF LIST:**
***

AbstractSequentialList -> DoublyLinkedList

* By having a dummy head and tail nocce, there is never a worry whether you are at the beginning or the end of the Linked_list, you know if you are or not, and the head and tail remain unchanged through any edit to the list: the only parts of the head and tail that will ever change is head.next and tail.previous.

```Java
public class DoublyLinkedList<E> extends AbstractSequentialList<E>
{
    private Node head;
    private Node tail;
    private int size;

    public DoublyLinkedList()
    {
        head = new Node(null);
        tail = new Node(null);
        head.next = tail;
        tail.previous = head;
        size = 0;
    }

    private class Node
    {
        public Object data;
        public Node next;
        public Node previous;

        public Node(Object data)
        {
            this.data = data;
        }
    }
}
```

* Helper methods which are private include:
    * They will not check for list bounds because those vary with the client methods (Ex) index size is allowed in add(), but not in remove() or set()... not changing size itself, only Linked-List edits or traversals inside.
1. Insert Node after current Node without incrementing size: O(1).
```Java
private void link(Node current, Node newNode)
	{
		newNode.next = current.next;
		newNode.previous = current;
		current.previous = newNode;
		current.next = newNode;
	}
```
2. Deleting a Node without updating size: O(1).
```Java
private unlink(Node current)
	{
		current.next.previous = current.previous;
		current.previous.next = current.next;
	}
```
3. Finding a specific Node by index: O(N).
```Java
private Node findByIndex(int pos)
	{
		for(int count = 0; count < pos; int++)
		{
			current = current.next;
		}
	}
```