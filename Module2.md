### Redis Commands

All of Redis commands can be find in their documentation. However for the ease of use, you could just filter out by data structure like strings, lists.

We will be going through some basic commands so we get an understanding of different types of data structures supported by Redis.

### Strings
```
SET name "John"                         
GET name
EXISTS name                            // Check existence of key
DEL name                               // Delete key 
EXPIRE name 5                          // Delete key when expired
SET counter 100
INCRBY counter 25                      // Increments by 25
DECR counter                           // Decrements by 1  
MSET a 10 b 20                         // Multiple SET
MGET a b                               // Multiple GET
```

### Lists
List of Strings sorted by their insertion order.
Redis lists are implemented using linked-lists rather than arrays. Therefore insertion happens in constant time while searching for key may take more time. Linked-lists implementation is used by Redis it allows to add elements quickly even to long list. However sorted-lists in Redis is recommended if you application would consistently search for elements.

Ideal For :-
 * Queues
 * Stacks
 * Top N recent News
 
 ```
 LPUSH :  Inserting Element from HEAD
 RPUSH :  Inserting Element from TAIL
 ```
 
```
LPUSH num 1 2 3 4                      // Add from left to head
LRANGE num 0 10                        // return value starting from index 0 to 10
LPOP num                               // pop value from the top
RPUSH num 5                            // push value from last
RPOP num                               // pop the value from the bottom
LLEN num                               // return length of the list
LINDEX num 3                           // return 
LSET num 0 5                           // Insert 5 at 0th index
LRANGE num 0 -1                        // return all elements of list
```

### Hashes

Hash map consists of field-value pairs.
```
HSET user name "Abhay"                // Set single field
HMSET user id 100 name "Alam"         // Setup hash with key "user"
HGET user id                          // Only 'id' field returned 
HMGET user id name                    // get values of that field
HGETALL user                          // return all field value
HEXISTS user id                       // check if key id exists
HDEL user name                        // delete key name
HSETNX user surname mm                // set if field doesnot exist
HKEYS user                            // show fields of user
HVALS user                            // show only values of user
HINCRBY user age 29                   // increment 
HLEN user                             // Number of field value pair
```
Sample Usage :-
* Saving properties of a Business Object
* 

### Sets

Sets are simply unordered collections of strings.Maintains unique set of items but unordered.
Supports intersections, unions.
Quickly check whether a member exist.

Ideal For :-
 * Storing relations (i.e. followers, friends)
```
SADD mySet 10 45 12                  // Add elements to set
SMEMBERS mySet                       // Get all members of the set
SISMEMBER mySet 10                   // Returns whether value exists
```

### Sorted sets
Same as Set but ordered.
The order is defined by score, Each memeber has a score assigned to.
Sorted sets are kind of in-between set and hash data structures, where each element consists of floating point value called ‘score’. This is ordered in term of this score value.
```
ZADD children 1992 "Sam"             // Birth-year acts as score
ZADD children 1997 "Tom"
ZRANGE children 0 -1                 // Returns all in order
ZREVRANGE children 0 -1 withScores   // Reverse order of ZRANGE
ZRANGEBYSCORE children -inf 1995     // Scores until 1993
ZREMRANGEBYSCORE children 1990 1995  // Remove from sorted set
ZRANK children "Tom"                 // Score rank of 'Tom'
```
