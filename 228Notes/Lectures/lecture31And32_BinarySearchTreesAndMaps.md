# 228 Notes: **WEEK 10** - Friday

## **BST'S AND MAPS:**
***

### **Binary Search Trees**

* successor() - returns a reference to the node that contains the successor of n.data (according to the natural ordering of T).
    * the node has a right subtree - go down to leftmost element in the right subtree (smallest element in its right subtree).
    * the node does not have a right subtree - then the node is the rightmost element of some subtree.  If there is actually a successor, then it must be the root of this subtree. 
        * to find this root, go up the tree following parent pointers, stopping when the previous node in the path is a left child of the current node - this current node is your root.
* successor() runtime - O(height(T))
* remove() runtime - O(height(T))
* add() - O(height(T))
* search() - O(height(T))
* BST iterator
    * the iterator should start at the minimum - or leftmost - element of the tree, and proceed all the way to the maximum - or rightmost - element. 
    * hasNext() and next() are easily implemented using successor().
    * remove() is implemented using unlinkNode(), with a little twist.
        * suppose we remove a node x with two children, then x is not actually removed. 
            * instead, its successor is copied into its place, which next() should return. Thus, we reassign the cursor to reference that node. 
    * runtime of a BST iterator
        * commonly O(log(n))
        * worst-case: O(n)
***

### **Maps**
* map - an object that maps a finite set of keys to a collection of values. 
    * each key can map to at most one value, and a map cannot contain duplicated keys. 
    * Ex) associating IP addresses (keys, Strings) to host names (values, Strings). 
    * Ex) associating social security numbers (keys, integers) to people's names (values, Strings). 

***

* public interface Map<K, V>
    * K - type of keys
    * V - type of values
* boolean containsKey(Object key) - returns true if this map contains a mapped value for this key.
* boolean containsValue(Object value) - returns true if this map contains one or more keys mapped to this value.
* V get(Object key) - returns the value to which the key is mapped, or null is this map contains no mapping for the key.
* boolean isEmpty() - returns true if this map contains no key-value mappings.
* V put(K key, V value) - associates the passed value with the passed key in the map. However, if the key is already being used, we replace the key's old value with the new value, and return the old value. 
* V remove(Object key) - removes the mapping for the passed key from this map if it exists.
* int size() - returns the number of values associated with keys (key-value mappings) in the map. 
* Set<K> keySet() - returns a Set view of the keys contained in this map.
* Collection<V> - returns a Collection view of the values contained in the map.
* Set<Map.Entry<K, V>>, entrySet() - returns a Set view of the mappings contained in the map. 

***

* Because put(), get(), contains(), and remove() all rely on linear scans, they all take O(n). 
    * note that we iterate over the set of keys, not over the key-value mappings. 