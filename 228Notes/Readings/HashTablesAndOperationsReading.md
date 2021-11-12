# 228 Notes: **WEEK 11** - Wednesday

## **HASH TABLES AND THEIR OPERATIONS (COLLISIONS, CHAINING, LINEAR PROBING):**
***

## **HASH TABLES BASICS**

* Hash table - a data structure that stores unordered items by mapping (hashing) each item to a location in an array (or vector).
* Key - in a hash table, an item's key is used to map an item to an index.
    * ideally every key is unique (more on that later). This is what allows a hash table to search for an item in O(1).
* Bucket - each element in a hash table
    * depending upon how coliisions are handled, a bucket may contain several items.
* Hash function - computes a bucket index from the item's key.

* Modulo operator - computes the integer remainder when dividing two numbers
    * Ex) a 20 element hash table with a hash function key of %20 will map keys to bucket indices of 0 to 19.

* Empty elements - empty elements are represented differently depending upon the kind of information is being stored.

### **REVIEW**

![](https://i.gyazo.com/cbda988fb023762138d0b74b110e60f9.png)

![](https://i.gyazo.com/031b90ec5d0ae7e01e107dd4bf91fcaf.png)

![](https://i.gyazo.com/d7c4b16dc356656027114f13edffb21c.png)

![](https://i.gyazo.com/c203f123d342ce0501226f7f4754e2a3.png)

***

## **COLLISIONS**

* Collision - occurs when an item being inserted into a hash table mapts to the same bucket as an existing item in the hash table.
    * Ex) for a hash function of key % 10, 55 % 10 = 5, but inserting 75 % 10 = 5 would map 75 to the same bucket.

***

## **CHAINING**

* Chaining is a collision resolution technique where buckets can have multiple elements in a list. 
    * the insert operation first uses the item's key to determine the bucket, and then inserts the item in that bucket's list. 
    * Ex) so bucket 5's list would become 55, 75.
* Open addressing - a collision resolution technique shere collisions are resolved by looking for an empty bucket elsewhere in the table 
    * Ex) so 75 might be stored in bucket 6.
* Searching when handling collisions with chaining first determines the bucket, and then searches the bucket's list.
    * the same applies for removes.

![](https://i.gyazo.com/1f886ae812c6e8f81f4be3170716dde4.png)

![](https://i.gyazo.com/9e91950950467802a62fb462dca8d3a4.png)

### **CODE**
![](https://i.gyazo.com/4dec990b102cc056d5a7d1cae82892f5.png)



***

## **LINEAR PROBING**

* Linear probing - handles a collision by staring at the key's mapped bucket, and then linearly searches subsequent buckets until an empty bucket is found.
    * however, there are two different kinds of empty buckets.
* Empty-since-start
    * a bucket that has been empty since the hash table was created.
* Empty-after-removal
    * a bucket that has had an item removed that caused the bucket to now be empty. 
> The distintion will be important during searches, since searching only stops for empty-since-start, and not for empty-after-removal.

***
### **HOW IT WORKS**
* Using a linear probing, a hash table insertion algorithm uses item's key to determine the inital bucket.
    * once finding the initial bucket, the algorithm then inserts the item in the next empty bucket (the kind of the empty bucket does not matter).
    * if the probing reaches the last bucket, the search continues at bucket 0. 
    * the insertion algorithm returns true if the algorithm was inserted, and false if it was unable to be inserted (meaning that the hash table is full).
* Using linear probing, a hash table removal aglorithm uses the item's key to locate the starting bucket.
    * once finding the inital bucket, the algorithm probes each bucket until either a matching item is found, or an empty-since-start bucket is found, or all buckets have been probed.
        * if an the item is found, the item is removed and the bucket is marked as empty-after-removal.
    * the removal algorithm does not take into account the type of the empty bucket.
* Using linear probing, a hash table search algorithm uses the sought item's key to determine the initial bucket.
    * Once finding the initial bucket the algorithm then probes each bucket until either the matching item is found (returing the item), an empty-since-start bucket is found (returning null), or all buckets have been probed without a match (returning null). 
        * If an empty-after-removal is found, the search algorithm conitnues to probe the next bucket. 

***
### **REVIEW**
![](https://i.gyazo.com/a40ae66ae85c60b726dcb7f82491d478.png)

![](https://i.gyazo.com/ffab837fc3eaf26b2727dbb0592757df.png)

![](https://i.gyazo.com/050b444b6e97891783c06a01c9c340d3.png)

![](https://i.gyazo.com/2821761ae6dbe8a614cdacdcada3b8c6.png)

![](https://gyazo.com/12643036d80a4666baffb2a2c6ba7b47)

![](https://i.gyazo.com/12643036d80a4666baffb2a2c6ba7b47.png)

***

## **HASH TABLE RESIZING**
* rezie - an operation that increases the number of buckets, while preserving all of the existing items present in the hash tasble before the operation. 
    * a hash table with N buckets is commonly resized to the next prime number >= N * 2.
    * a new array is allocated, and all items from the old array and re-inserted into the new array using the new key value for the hash table.
        * This results in a time complexity of O(N). 

### **WHEN TO RESIZE**
* There are three main ways to assess when to resize the hash table. 
    * load factor - the number of items in the hash table divided by the number of buckets.
    * the number of collisions during an insertion
        * open-addressing
    * the size of a bucket's linked-list
        * chaining

*** 
### **REVIEW**
![](https://i.gyazo.com/ef88f7347a3a4eb1b8abe1c540d03032.png)

![](https://i.gyazo.com/08d4ee322981aee839073e3c9cb654cf.png)