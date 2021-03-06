# 228 Notes: **WEEK 11** - Monday

## **HASH TABLES - THE "MAGIC" DATA STRCTURE:**
***
* hash tables are "magic" in that the average case is as fast as it could be, O(1), but the worst case is still as bad as any other data structure.
* **hashing function** - a function that takes some object and produces an integer (possibly a very large integer). A hash function usually converts an object into a very large integer, which then performs modulo backing_array_size to produce the element's / key object's index (bucket).
    * must operate in O(1).
    * it always prodicues the same integer from the the same object and should also change the output if the input changes just a tiny bit.
    * an analogus function is the checksum function that you can use when you download Linux images, which are one GB large, are processed to produce a 256 or 512 character signature that is called the checksum.
        * however they made that checksum method, one byte of a difference in the original image means that the checksum changes.
    * similarly, a hash function should produce the same number from any particular object.
* **hashing** - conveting a key object into an integer.
* worst case scenario for a hash table - two or more key objects are hashing to the same integer, therefore competing for the same slot (bucket) in the backing array. 
    * in the absolute worst case, the entire set of key objects all map to the same index (bucket).
    * often, they are attached as a single-linked-list, hanging off of that index / slot number (bucket).
        * when a linked-list is used to accomondate collisions (chaining)
* the reasons that we blow up the space of integers by making very large ones, is that it is statistically less likely that these numbers will collide after modulo some_small_number_buckets has been applied!

***
### **How do Hash Tables Relate to Maps**
* with maps, we can use custom labels.
    * Model_String is the key
    * Repair_Information is the value in the map
* hash tables are maps implemented as arrays in the backend - they use a hash function to convert the key into a specific integer index into the array. If the keys are spread to different spots, then look up, add, and remove are all O(1)... instantaneous operations!

***
### **Chaining v. Linear Probing**
* mitigating collisions is the main engineering question when working with hash tables.
* **chaining** - one of two ways of handling collisions in a hash table in which key objects that map to the same bucket are stored inside of a singly-linked-list that is attached to the corresponding bucket.
    * our search expectation is O(n).
        * even if we used a fancy data structure (like a splay tree) in place of the singly-linked-list, our search expectation would still be O(n) because we would still have to traverse the whole tree and search the keys one by one (linearly).
    * array slots are called "buckets" as it is a direct analogy to rifling through a bucket of sundries at a workshop to find a particular wrench.
* linear probing - the second way of handling collisions in a hash tables in which buckets can only contain one key object. If a key object is hashed to the same bucket, then the hash table will be sequentially probed (move to the next index) until a free index is found, in which the colliding object key is then placed.
    * "Ridiculous excuse of a accomondation technique, courtesy of the land of extremely mentally challenged computer scientists." - Georgi Batinov November 15, 2021.
    * how do we find an element in a hash table using linear probing?
        * we compute the hash result, then check the corresponding array slot (bucket). If the number is not there or the bucket is occupied, then we start wealking through the indices, probing each one in-turn. We stop once we have either found an empty slot or have looped around and ended up at the original index (bucket).
    * there are two different kinds of empty buckets when using linear probing
        * empty-from-deletion buckets
        * empty-since-start buckets
    * it turns out, that in the real world after we have applied all of the other mitigation techinques, linear probing is super fast compared to chaining - it is up to thousands of times faster than chaining (in practical terms), but in theoretical Big-O analysis, both have equally bad O(n) search / insert / delete.
        * intuition for this - cache locality on the processor
            * this means that the hash table is loaded IN the processor and is not even in memory... which means that each probe takes 1/1000th of the time it would take to go to memory.

***
### **Ordering in a Hash Table**
* the hash function is reapplied when we rehash the table, which we do when the hash table grows too large or too small.
    * if the number of keys becomes large in comparison to the number of buckets, the probability of collisions increases. A ratio of the number of key objects / number of buckets is called the load factor. 
* **load factor** - the number of key objects / the number of buckets.
* Java doubles the size of a hash table if the load factor exceeds 0.75 (and shrinks it if the load factor drops below a certain threshold).
    * after a new array has been allocated, all existing key-value pairs need to be rehashed.
