# Hash Tables

## What are they? How do they work?

A hash table is a really cool way of storing key/value pairs. It uses an array as the base data structure. Remember that looking up a value in an array (if you know the index) happens in O(1) time. However this is if you know the index. A hash table allows you to set a key where the index of the unordered array the value is being stored in is derived from that key using a hashing algorithm. When you store the value in the array you run the hashing algorithm to derive the index from the key, and when you want to retrieve the value again you can use the hashing algorithm once again to derive the index from the key again.

Confused? Me too. Let's look at an example of how this works. Let's say we have a list of data, idk maybe it's customers or something, and each customer has a customer ID. We're pulling the details of a couple of those customers in to memory. Doesn't matter, we only care about the fact that we have customer IDs right now. The first step is to create the underlying array, let's say 10 elements.

<table><thead><tr><th width="59">0</th><th width="60">1</th><th width="60">2</th><th width="60">3</th><th width="60">4</th><th width="60">5</th><th width="60">6</th><th width="60">7</th><th width="60">8</th><th width="60">9</th></tr></thead><tbody><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr></tbody></table>

The first customer id we want to store is 47. How do we know what index to put it in? We're going to use a simple modulus algorithm. Why modulus. Because this allows us to set the upper bound for the indexes based on the array length. The function `I = N % 10` (where I is the index, and N is the customer ID) will always result in an index that is greater than or equal to 0, and less than 10. We'll never get an index that is greater than or equal to the length of the array. Which would be bad, that's how you get an out of bounds exception. In this case insertion is O(n) constant time, we run `I = N % 10` and get an index of 7, and insert that value at index 7.

<table><thead><tr><th width="59">0</th><th width="60">1</th><th width="60">2</th><th width="60">3</th><th width="60">4</th><th width="60">5</th><th width="60">6</th><th width="60">7</th><th width="60">8</th><th width="60">9</th></tr></thead><tbody><tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td>47</td><td></td><td></td></tr></tbody></table>

Now let's use the ids 29, and 3254, and 1000000.

The resulting indexes are 9, 4, and 0. Let's insert those in to our array.

<table><thead><tr><th width="100">0</th><th width="55">1</th><th width="55">2</th><th width="55">3</th><th width="65">4</th><th width="55">5</th><th width="55">6</th><th width="55">7</th><th width="55">8</th><th width="57">9</th></tr></thead><tbody><tr><td>1000000</td><td></td><td></td><td></td><td>3254</td><td></td><td></td><td>47</td><td></td><td>29</td></tr></tbody></table>

You'll notice that while they aren't in order, it's still extremely easy to access these values by their index, by just deriving their index from the customer ID when we want to look up the customer information again. It's even better than the O(log N) for a binary search, and it is unordered.

## Collisions

"But Kyle", you might say, "what happens when you get the same index from different IDs?"

"That's a great question", I might say, "unfortunately that's one of the universes greatest mysteries".

### Chaining

Just kidding, it's called a collison. There is a couple ways of handling this. Chaining, and open addressing are two common ways. In open addressing you just add it to the next available index. Chaining is where you store a list of values at that index, which still keeps the lookup time as O(N) where N is the number of values at that index.&#x20;

### Linear Probing

Linear probing is the process of searching for the next available index to store a value in the case of a collision. In our example above if we tried to store a value for the key 54 it would be stored in the 5th index instead when it collides with 3254 in the 4th index.

### Quadratic Probing

Another way to find a new index to store the value at is by using the formula `I = (p + c1 * i + c2 * i^2) % L` where:

* I = the new index we're trying to find
* p = the previous index we determined to already be taken
* c1 = a random constant
* i = how many iterations we've had to probe so far
* c2 = a random constant
* L = the length of the array

Let's try this in the case of our key of 54. We haven't probed yet, so i = 0. Let's pick two random constants. c1 will be 3 and c2 will be 7.&#x20;

`(4 + 3 * 0 + 7 * 0^2) % 10 = 4` Oops, we collided again. Let's increment i and try again.

`(4 + 3 * 1 + 7 * 1^2) % 10 = 4` Uh, okay seriously another collision? Let's increment i again...

`(4 + 3 * 2 + 7 * 1^3) % 10 = 8` Index 8 is free! Yay!

### Double Hashing

Double hashing is similar to quadratic probing where it uses 2 different hashing function (h1 and h2) and also iterates until it finds and open index. The formula is `(h1(key) + i * h2(key)) % L`.

It's also worth noting that you can have another hash table as the value of a hash table where a value is stored at `h1(key)` of the first hash table, and `h2(key)` of the nested hash table.

### Resizing

Typically hash tables are resized to the next prime number that is greater than or equal to the current length multiplied by 2. In our case the next prime number would be 11, and 11\*2 is 22. We would resize the hash table to a length of 22.

When do you resize a hash table?

You typically resize a hash table when a certain defined threshold is met for&#x20;

* The number of iterations required to find an open index when a collision occurs using open addressing.
* The number of nodes in a list at a collided index when using chaining.
* Or the hash tables load factor.

The load factor is the number of items in a hash table divided by the length of the hash table. In our example (after inserting key 54) that is 5 values stored and a length of 10, so a load factor of 50%.

## Common Hashing Functions

### Good Hash Function

A good hash function is one that minimizes collisons, it does this by distributing the keys as evenly across the indexes as possible. This also has the side effect of making the function as fast as possible as well.

A perfect hashing function is one that never collides ever. The only way to have a perfect hashing function is by knowing the number of all the items and all of the possible item keys before hand.&#x20;

This is why hash tables are O(1) in a perfect world, and O(n) in the worst case scenario.

### Modulo Hash Function

A modulo hash function is exactly what we've been using throughout all of the examples on this page. Its main purpose is ensuring that the resulting index is always equal to or greater than 0, and less than the length of the underlying array.

### Mid-square Hash Function

A mid-square hash function works by squaring the key, taking R amount of digits from the center of the resulting square as the index. For example if we were getting the index for key 458 in a hash table with a length of 100 using R = 2 we would get 458 \* 458 = 209,764, the mid square would be 2 digits from the center = 97. In order for a mid-square function to work R must be greater than or equal to `log 10 L` where L is the length of the hash table.&#x20;

This is a base 10 implementation of a mid-square function, although typically a base 2 mid-square hash function is implemented.

### Multiplicative String Hash Function

A multiplicative string hash function works well on short english strings. It requires setting the string hash to an initial value, and defining a hash multiplier first. It then iterates over each character in the string key. Each iteration changes the string hash value to `C * M + V` where:

* C = current string hash value
* M = multiplier
* V = the ASCII or Unicode value of the current iterations character

Of course you then do need to apply the modulus function of `C % L` where:

* C = current string hash value
* L = length of the table hash

To ensure the resulting index stays in bounds.&#x20;

Daniel J. Bernstein foundf that using an initial value (C) of 5381 and a multiplier of 33 (M) performs excellent agains short english keys. You'll notice that when defining variables like this in hashing functions they're typically always prime. This is of course due to a prime numbers unique divisiblity properties when using modulus and helps distribute keys across the available indexes.



\--TODO: hashing attacks ddos: [https://www.reddit.com/r/algorithms/comments/17zcylu/why\_time\_complexity\_of\_hashmap\_lookup\_is\_o1\_not/](https://www.reddit.com/r/algorithms/comments/17zcylu/why_time_complexity_of_hashmap_lookup_is_o1_not/)



