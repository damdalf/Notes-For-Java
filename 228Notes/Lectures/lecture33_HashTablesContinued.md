# 228 Notes: **WEEK 11** - Wednesday

## **HASH TABLES CONTINUED:**
***

### **Quick Review**
* Review of hashing
    * Take an object, and convert it to a large integer. Then, apply modulo array_size.
* Collision is the primary problem when working with hash tables.
    * Collision - when two or more keys map to the same index (bucket) of the backing array. 
***

### **Handling Collisions**
* There are two ways to handle collisions:
     * Chaining - puts colliding key-value pairs in a singly-linked list in the bucket where the collision(s) occurred.
        * Other data structures than the singly-linked list do not offer any extra benefits, stick to using the singly-linked list.
                * We still need to compare each unique key to all present keys at that hash address.
    * Linear-probing - put only one key-value pair in each index, and if we find an occupied slot while searching for a place to dump our payload, we then linearly search the hash tble until we find a sequential bucket that is empty.
         * If we reach the end of the hash table without finding an empty bucket, we then wrap around to the beginning of the hash table begin searching from the beginning.
         * Stupid idea, but it works prefectly in real-world applications (linear-probing has hardware advantage compared to chaining).
         * In linear-probing, there are two different kinds of empty buckets:
            * Empty-since-start
            * Empty-from-deletion
        * How do we handle the situation where a displaced key has been preceded by a deleted key?
            * The simplest technique is called 'tombstone-hashing'. 
         * tombstone-hasing - we replace deleted keys with a key-value special object acting as a 'Deleted' marker, also known as 'Empty-from-deletion'. 
             * Then, the algorithm searching for the key does not terminate when it sees that marker and will not terminate until it sees an actual empty slot, which is known as 'Empty-since-start'.
              * However, we cannot have too many tombstones because that makes the search chains too long; so we set a level of saturation at which we will rehash the table and delete all tombstone indicies.
         * In practice, linear-probing is preferred to chained hashing. The reason is that other mitigation techniques make the worst cases unlikely, AND linear-probing has a hardware advantage: we can load large portions of a hash table in the processor cache, and working on it takes 1/1000th of the time to go fetch the next node in a linked list in memory.
            ***

### **Mitigating Collisions**
* How do we mitigate collisions?
    * Two main ways, which should be used together.
        * Pick a good hash function
        * Rehash the table when the payload ratio becomes too high
    * What is the purpose of hash function?
        * The job of a hash function is to avoid patterns. Most data in the real world has patterns because it has been loaded from some database.
            * Random() would be an exceptionally good hash function, BUT it is not deterministic, so we cannot reuse it on the same key.
* Two examples of *BAD* hash functions:
    * If our keys are Strings:
        * 1) Convert the String to a sum of ASCII values of the characters.
            * Issues: anagrams maps to the same slot:
                * 'tap' vs 'apt' vs 'pat'
        * 2) Pick the first three letters of the String and have them have their own slot. 
            * Issues: If there are many Strings that start with 'pre', then there will be many empty slots such as 'xzq' 'zqx'.
                * We will have a non-uniform skewed distribution of keys to array indices!
***

### **What Does a Good Hash Function Look Like?**
* Properties of a good hash function:
    1. The hash function must create a uniform distribution of keys to array slots, ideally 0 or 1 key per each slot (bucket).
        * BUT, even if we had 12 keys in EVERY slot, the hash tables will still be blindingly fast! However, this can become false if the amount of keys to array slots is not consistent across the entirety of the backing array.
    2. The hash function must be deterministic (cannot use Random() even though it is perfect for the first condition!).
    3. The hash function needs to be computed easily in O(log(n))
    4. The has function must use prime numbers because they are the least likely to be involved in data patterns, because they have no actual divisors.
        * Primes are the 'Noble elements' of numbers in the sense that they are the least likely to be parts of patterns.
        * Marsenne Primes - prime numbers that have the form:
            * 2^(k) - 1
                * Ex) 31
                * Ex) 127
                * Ex) 255
        * The reason that we care about powers of two is because we are trying to exploit hardware efficiencies with bit-shifting numbers, e.g. you can use 32 or 127 by getting a full bit String of size 5 or 7.
***

### **Important Ideas** If a hash function's worst-case (or any of the hash tables methods) exceeds O(1), using a hash table is pointless. If this is true, then you should be using a splay tree.
***

### **HashCode for Any Object**
* General case:
    * We can write a hash function for any arbitrary object using the String.hashCode() inuition.

```java
hashCode()
{
    hash = some initial value like 0;
    for each instance variable v used by equals()
    {
        c = v.hashCode();
        hash = hash * 31 + c;
    }
    return hash;
}
```

* hashCode() for primitives:
    * v is a short, char, or byte: 
        * Set c = (int) v
    * v is a boolean:
        * Set c = (v? 0:1). 
            * If true, c = 1, if false, c = 0.
    * v is a float:
        * Set c = Float.floatToIntBits(v)
***

### **Load Factor**
* Load factor - the ratio of: the number of key-value pairs / the number of buckets in the backing array.
* Java doubles the size of the backing array and rehashes the existing key-value pairs when load factor exceeds 0.75.
    * Space doubling and rehashing happens in amortized O(1) for the exact same reasons as checkCapacity() for ArrayList.
    * However, the ordering in hash tables is not guarranteed because of the periodic rehashing which canges the hash number, and results in key-value pairs being hashed to different buckets.
        * If you need an unchanging order of listing the elements in a hash table, use TreeMap or LinkedHashMap.
