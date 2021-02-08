
# Probabilistic Data structures in Analysis of Big Data
Big data is a collection of large amount of data which increases in volume, velocity and variety. In this blog discuses the methods of using Probabilistic Data Structure in Big Data Analysis and primarily focused on **Bloom Filter** which decreased the space or time.

The conventional data structures and algorithm are not sufficient to manage larger and more complex dataset of Big Data.

## What is PROBABILISTIC DATA STRUCTURE
Data structures are nothing different. They are like the bookshelves of your application where you can organize your data. Different data structures will give you different facility and benefits. 

The main-stream data structures like Lists, Maps, Sets, Trees etc. are mostly used for achieving certain results about whether the data exist or not, maybe along with their number of occurrences and such.

But these Data Structures are not suitable for analysis of the huge capacity of Big Data because the computational and time complexity is large. Probabilistic Data Structure is more efficient of constant run time.

**PROBABILISTIC DATA STRUCTURE**  are based on hash functions to represent a set of elements randomly. They provide answer approximately. They use much less memory and constant query time. Probabilistic Data Structure can be paralleled that's the way it's  suitable for Big Data Analysis and Processing.

## Bloom Filter
A Bloom Filter is a probabilistic data structure to test whether data belong to a data set by using multiple hash functions. 

 - Bloom Filtering Technique is used to test whether an element is a member of a set. It returns two types of results false positive or false negative.
 - Bloom Filter is used to check membership of an element E in a set of S elements.
 - Bloom Filter consists of a data set consisting of 0's or 1's and some
   hash functions.
 - In Bloom Filter the number of hash function depends on the required accuracy of bloom filter. Other factors impacting the accuracy of bloom filter are size of the data set and number of elements added to the set.
 - 

## Bloom Filter Works:

 - You initiate an empty bit array of length m.
 - you select k different hash functions (the more independent the better)
 - if you want to add an element, you calculate all the k hashes of this value and set the corresponding bits to 1
 - To test whether it is in the set, feed it to each of the  _k_  hash functions to get  _k_  array positions
-   If any of the bits at these positions is 0, the element is definitely not in the set
-   if all the bits would have been set to 1 when it was inserted. If all are 1, then either the element is in the set, or the bits have by chance been set to 1 during the insertion of other elements.


> The classic example of using bloom filters is to reduce expensive disk
> (or network) lookups for non-existent keys. As we can see that bloom
> filters can search for a key in O(k) constant time, where k is the
> number of hash functions, it will be very fast to test non-existence
> of a key.

Understand by Example:
Suppose you are creating an account on any "Social Media", you want to enter a cool username, you entered it and got a message, “Username is already taken”. You added your birth date along username, still no luck. Now you have added more information, still got “Username is already taken”. It’s really frustrating, isn’t it? But have you ever thought how quickly "Social Media" check availability of username by searching millions of username registered with it. There are many ways to do this job –
 

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI1MTAxNjI2NywtMTk0MjI4MzIyMCwtND
IyMzE4OTk0LC0zMjQyODA3MzAsLTIxMTQ1MDA0ODMsLTIxMjI0
NjU3ODEsNDU4ODkwMDEzLC0xNjU2ODc3MDEwLDExODM0NTIzND
gsLTE4OTU5ODk1NTEsMjExNzgxMjg4MSwxNTA1MjcwMjk2LC0x
OTY4NjcxNzMsLTYzNzMzNjAwNiwtODIyODE4MjQwLC0yMDczMz
U0Njc4LDEyNTc5MTM3NjgsLTczNDI2MzE5MywxNzE3MjE5Nzc0
LC05Mzk3MzYxNThdfQ==
-->