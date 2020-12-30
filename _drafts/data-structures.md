---
layout: default
title: Sorting Algorithms
permalink: /tutorials-cheat-sheets/data-structures-and-algorithms/sorting-algorithms/
parent: Data Structures and Algorithms
grand_parent: Tutorials and Cheat Sheets
has_children: false
nav_order: 2
nav_exclude: false
has_toc: false
---

# Data Structures

The fundamental data structures fall into 4 categories:
- Linear data structures
  - Arrays (dynamic)
  - Linked Lists (singly, doubly, etc.)
  - Stacks
  - Queues
- Tree data structures
  - Binary Search Trees
  - Heaps (binary)
- Hash data structures
  - Hash Tables
- Graph data structures
  - Graphs

Although software is not limited to these data structures, the structures listed above are enough to give you a proper foundation if you choose to branch out.

The time and space complexities of some popular data structures can be seen in the image below:

<p align="center">
    <img src="/assets/images/data-structures-and-algorithms/data-structures/data-structure-complexity-chart.png" alt="data-structure-complexity-chart.png"/>
    <br />
    <a href="https://www.bigocheatsheet.com">source: bigocheatsheet.com</a>
</p>

Before moving on, it is important that you know how to interpret the above table. In terms of time complexity:
- Accessing (AKA indexing): Given an index, find the corresponding value
- Searching: Given a value, find a match
- Inserting: Given a value, insert it into the data structure
- Deleting: Given a value, delete it from the data structure

These operations are fundamental to most data structures. However, there are exceptions. For example, from the table, you may notice that data structures such as the hash map do not have "access" functionality.

Even with these definitions, the complexities on the above table can be misleading. The complexities of data structures depends on their specific implementations so the values on this table should be seen as "typical" approximations. For example, the `O(1)` insertion time complexity for linked lists assumes that you already have a reference to the node you're inserting after. Typically, when adding/removing data to/from a linked list, a sequential search is required to find the desired position for insertion/deletion. This would make these operations `O(n)` rather than `O(1)`.

Regarding space complexity, all the fundamental data structures discussed below have `O(n)` space complexity. A location in memory is required for each value stored in the below data structures.

In this section, we'll be going over the fundamental data structures. However, descriptions are not enough. I find that the best way to learn how a data structure works is to implement it yourself in your preferred programming language. To serve as examples, I've implemented all data structures covered in this tutorial using Java. Why Java? It's more hands-on than Python but not as complex as C++. It's easy to read and similar in syntax to other popular programming languages. It's also my first and preferred object-oriented programming language.

For additional resources, [GeeksForGeeks](https://www.geeksforgeeks.org/data-structures/) has extensive documentation on data structures. Including sample implementations in a variety of languages. They also have quizzes and practice questions to help you hone your skills. Additionally, [mycodeschool](https://www.youtube.com/user/mycodeschool) is a youtube channel with plenty of quality video tutorials on data structures.

# Arrays (Dynamic)

<p align="center">
    <img src="/assets/images/data-structures-and-algorithms/data-structures/array.png" alt="array.png"/>
    <br />
    <a href="https://www.geeksforgeeks.org/array-data-structure/">source: geeksforgeeks</a>
</p>

Arrays are typically primitive data types so they have little functionality out of the box. Primitive arrays can't perform fundamental data structure operations such as `searching`, `inserting`, and `deleting`. Therefore, when "arrays" are compared to other data structures, the comparison typically refers to dynamic arrays such as an ArrayList or Vector. An ArrayList/Vector is essentially just an array that has been extended to perform the fundamental data structure operations. Arrays have many [applications](https://www.thecrazyprogrammer.com/2020/04/applications-of-array.html). Particularly, they are used as lists and to implement a variety of other complex data structures. If you're at the point where you're learning data structures and algorithms, you likely already know what an array is. If not, refer to the [GeeksForGeeks documentation](https://www.geeksforgeeks.org/array-data-structure/) or the [mycodeschool video tutorial](https://www.youtube.com/watch?v=5tPLyHCZdU0).

My example implementation of an ArrayList can be found [here]().

Worst/Average Case Array Time Complexity:
- Indexing - `O(1)`
  - Given an index, you can immediately find the value.
- Searching - `O(n)`
  - Given a value, an array must be sequentially searched for a match. In the worst case, there is no match and the entire array is traversed.
- Inserting - `O(n)`
  - In the worst case, the insertion happens at the first index and all elements must be moved up by one index.
- Deletion - `O(n)`
  - In the worst case, the deletion happens at the first index and all elements must be moved down by one index.

Note that some implementations of dynamic arrays double their size when they reach max capacity. As such, when there is space remaining in the array, insertion complexity is `O(1)`. When there isn't space and the array must be resized, the time complexity is `O(n)`. Having scenarios that result in different time complexities is referred to as `amortized` time complexity.

# Linked Lists

<p align="center">
    <img src="/assets/images/data-structures-and-algorithms/data-structures/linked-list.png" alt="linked-list.png"/>
    <br />
    <a href="https://www.geeksforgeeks.org/data-structures/linked-list/">source: geeksforgeeks</a>
</p>

While arrays store data elements in contiguous memory locations, linked lists store data elements in contiguous nodes that are connected via pointers. There are 3 main types of linked lists:
- Singly Linked List (Nodes points to the next node)
- Doubly Linked List (Nodes points to the next and previous node)
- Circular Linked List (Singly or doubly linked list where the "last" node points back to the head instead of null)
Linked lists have many [applications](https://www.geeksforgeeks.org/applications-of-linked-list-data-structure/). Particularly, they are used as lists and to implement a variety of other complex data structures. For more information, see the [GeeksForGeeks documentation](https://www.geeksforgeeks.org/data-structures/linked-list/) or the [mycodeschool video tutorials](https://www.youtube.com/watch?v=NobHlGUjV3g&list=PL2_aWCzGMAwI3W_JlcBbtYTwiQSsOTa6P&index=3).

My example implementations of the above linked lists can be found [here]().

Worst/Average Case Linked List Time Complexity:
- Indexing - `O(n)`
  - Given an index, a linked list must sequentially traverse nodes starting from the head to locate the indexed node.
- Searching - `O(n)`
  - Given a value, a linked list must sequentially search to find a matching value. In the worst case, there is no match and the entire list is traversed.
- Inserting - `O(1)`
  - Assuming insertion involves a referenced node (such as the head), it has constant time complexity. However, if you do not have a refence to a node adjacent to the desired insertion location, a sequential search is required to find it resulting in an `O(n)` time complexity.
- Deletion - `O(1)`
  - Assuming deletion involves a referenced node (such as the head), it has constant time complexity. However, if you do not have a refence to a node adjacent to the desired deletion location, a sequential search is required to find it resulting in an `O(n)` time complexity.

From my example implementations, you may have noticed that arrays and linked lists can perform the same functions. However, their differences provide them with distinct advantages and disadvantages. As such, there are situations where using one over the other is beneficial:'
- Arrays should be used when:
  - Indexing is a major operation
    - When indexing, arrays have an unbeatable constant time complexity of `O(1)`. Linked lists have a mediocre linear time complexity of `O(n)`.
  - The number of elements to be stored is known (i.e. array size known)
    - When arrays are at full capacity, they use less memory than linked lists.
- Linked lists should be used when:
  - The number of elements to be stored is unknown
    - When arrays are at below full capacity, the use more memory than linked lists. This is because arrays must be defined at a fixed size. When an array is created, memory corresponding to each element is allocated regardless of whether it is filled with useful data.
  - Constant time insertions/deletions are required
    - When inserting/deleting around a referenced node such as the head, linked lists have a constant time complexity of O(1). Otherwise, linked lists and arrays both have linear time complexities of `O(n)`. 

Arrays and linked lists are the most important data structures to be familiar with. This is because the other fundamental data structures are implemented using their underlying principles. Make sure you have a good grasp of these data structures before moving on.

# Stacks

<p align="center">
    <img src="/assets/images/data-structures-and-algorithms/data-structures/stack.png" alt="stack.png"/>
    <br />
    <a href="https://www.geeksforgeeks.org/stack-data-structure/">source: geeksforgeeks</a>
</p>

Stacks are what's known as a LIFO (last in, first out) data structure. An easy visualization is a stack of paper where each piece of paper represents an element stored in the stack. When a element is added to a stack, it is placed on top (i.e. `push()`). When an element is removed, it is taken from the top (i.e. `pop()`). As such, the latest element to join the stack is the first to leave. Hence the title LIFO. Stacks have many [applications](https://www.thecrazyprogrammer.com/2016/04/applications-of-stack.html). The most well known is "backtracking" which makes features such as "undo" possible. If you store your previous actions in a stack, they can be easily back tracked. For more information, see the [GeeksForGeeks documentation](https://www.geeksforgeeks.org/stack-data-structure/) or the [mycodeschool video tutorials](https://www.youtube.com/watch?v=F1F2imiOJfk&list=PL2_aWCzGMAwI3W_JlcBbtYTwiQSsOTa6P&index=14).

My example implementations of stacks can be found [here](). Note that a stack can be implemented using either an array or a linked list.

Worst/Average Case Stack Time Complexity:
- Indexing - `O(n)`
  - Given an index, a stack must sequentially search itself to locate the corresponding value.
- Searching - `O(n)`
  - Given a value, a stack must sequentially search itself to locate the corresponding value.
- Inserting - `O(1)`
  - Since stacks always add to the top (an easily indexable location), they have a constant insertion time complexity `O(1)`. 
- Deletion - `O(1)`
  - Since stacks always remove from the top (an easily indexable location), they have a constant deletion time complexity `O(1)`. 

# Queues

<p align="center">
    <img src="/assets/images/data-structures-and-algorithms/data-structures/queue.png" alt="queue.png"/>
    <br />
    <a href="https://www.geeksforgeeks.org/queue-data-structure/">source: geeksforgeeks</a>
</p>

Stacks are what's known as a FIFO (first in, first out) data structure. An easy visualization is a line at the grocery store where each person represents an element in the queue. When a person joins the queue (i.e `enqueue()`), they stand at the rear. When a person leaves the queue (i.e. `dequeue()`), it is from the front. As such, the first person to join the queue is the first person to leave. Hence the title FIFO. Queues have many [applications](https://www.geeksforgeeks.org/applications-of-queue-data-structure/?ref=rp). They are particularly useful for queuing processes that do not need to be executed immediately. For more information, see the [GeeksForGeeks documentation](https://www.geeksforgeeks.org/queue-data-structure/) or the [mycodeschool video tutorials](https://www.youtube.com/watch?v=XuCbpw6Bj1U&list=PL2_aWCzGMAwI3W_JlcBbtYTwiQSsOTa6P&index=22).

My example implementations of queues can be found [here](). Note that a queue can be implemented using either an array or a linked list.

Worst/Average Case Queue Time Complexity:
- Indexing - `O(n)`
  - Given an index, a queue must sequentially search itself to locate the corresponding value.
- Searching - `O(n)`
  - Given a value, a queue must sequentially search itself to locate the corresponding value.
- Inserting - `O(1)`
  - Since queues always add to the rear (an easily indexable location), they have a constant insertion time complexity of `O(1)`. 
- Deletion - `O(1)`
  - Since queues always remove from the top (an easily indexable location), they have a constant deletion time complexity of `O(1)`. 

# Binary Trees

<p align="center">
    <img src="/assets/images/data-structures-and-algorithms/data-structures/binary-tree.png" alt="binary-tree.png"/>
    <br />
    <a href="https://www.geeksforgeeks.org/binary-tree-data-structure/">source: geeksforgeeks</a>
</p>

Binary trees are the simplest for of tree data structure. As such, they are useful to cover in terms of understanding tree theory. They are particularly useful at storing hierarchical data. However, refering to binary trees simply as a "fundamental data structure" is a bit misleading. Binary trees are not really used for practical applications. Instead, they are the cornerstone to an entire family of more complex/useful data structures such as the binary search trees and heaps. For more information, see the [GeeksForGeeks documentation](https://www.geeksforgeeks.org/binary-tree-data-structure/) or the [mycodeschool video tutorials](https://www.youtube.com/watch?v=qH6yxkw0u78&list=PL2_aWCzGMAwI3W_JlcBbtYTwiQSsOTa6P&index=25).

My example implementations of queues can be found [here](). Note that a binary tree can be implemented using either an array or a linked list.

# Binary Search Trees (BST)

<p align="center">
    <img src="/assets/images/data-structures-and-algorithms/data-structures/binary-search-tree.png" alt="binary-search-tree.png"/>
    <br />
    <a href="https://www.geeksforgeeks.org/binary-search-tree-data-structure/">source: geeksforgeeks</a>
</p>

Binary search trees have many [applications](https://www.geeksforgeeks.org/applications-of-bst/). They are particularly useful for maintiaining a sorted list of data. For more information, see the [GeeksForGeeks documentation](https://www.geeksforgeeks.org/binary-search-tree-data-structure/) or the [mycodeschool video tutorials](https://www.youtube.com/watch?v=pYT9F8_LFTM&list=PL2_aWCzGMAwI3W_JlcBbtYTwiQSsOTa6P&index=27).

My example implementations of binary search trees can be found [here](). Note that a binary search tree can be implemented using either an array or a linked list.

Binary Search Tree Time Complexity:
- Indexing - Worst case:`O(n)`, average case:`O(log(n))`
  - Given an index, 
- Searching - Worst case:`O(n)`, average case:`O(log(n))`
  - Given a value, 
- Inserting - Worst case:`O(n)`, average case:`O(log(n))`
  - A
- Deletion - Worst case:`O(n)`, average case:`O(log(n))`
  - A

# Heaps (binary)

<p align="center">
    <img src="/assets/images/data-structures-and-algorithms/data-structures/min-and-max-heap.png" alt="min-and-max-heap.png"/>
    <br />
    <a href="https://www.geeksforgeeks.org/heap-data-structure/">source: geeksforgeeks</a>
</p>

http://souravsengupta.com/cds2016/lectures/Complexity_Cheatsheet.pdf

Heaps have many [applications](https://www.geeksforgeeks.org/applications-of-heap-data-structure/). They are particularly useful for implementing priority queues. For more information, see the [GeeksForGeeks documentation](https://www.geeksforgeeks.org/heap-data-structure/) or the [HackerRank video tutorial](https://www.youtube.com/watch?v=t0Cq6tVNRBA).

My example implementation of a heap can be found [here](). Note that a heap can be implemented using either an array or a linked list.

Binary Heap Time Complexity:
- ?

# Hash Tables

<p align="center">
    <img src="/assets/images/data-structures-and-algorithms/data-structures/hash-table.png" alt="hash-table.png"/>
    <br />
    <a href="https://www.geeksforgeeks.org/hashing-data-structure/">source: geeksforgeeks</a>
</p>

Hash tables have many [applications](https://afteracademy.com/blog/applications-of-hash-table). It is particularly useful for solving technical interview questions. For more information, see the [GeeksForGeeks documentation](https://www.geeksforgeeks.org/hashing-data-structure/) or the [Paul Programming video tutorial](https://www.youtube.com/watch?v=MfhjkfocRR0).

My example implementations of a hash table can be found [here]().

Hash Table Time Complexity:
- Indexing - N/A (There is no indexing, only searching via key)
- Searching - Worst case:`O(1)`, average case:`O(log(n))`
  - Given a value, 
- Inserting - Worst case:`O(1)`, average case:`O(log(n))`
  - A
- Deletion - Worst case:`O(1)`, average case:`O(log(n))`
  - A

# Graphs

<p align="center">
    <img src="/assets/images/data-structures-and-algorithms/data-structures/graph.png" alt="graph.png"/>
    <br />
    <a href="https://www.geeksforgeeks.org/graph-data-structure-and-algorithms/">source: geeksforgeeks</a>
</p>

Graphs have many [applications](https://www.geeksforgeeks.org/applications-of-graph-data-structure/). They are particular useful for relating data in a web-like formation. For example, web pages in the World Wide Web or users in a social media site. For more information, see the [GeeksForGeeks documentation](https://www.geeksforgeeks.org/graph-data-structure-and-algorithms/) or the [mycodeschool video tutorials](https://www.youtube.com/watch?v=gXgEDyodOJU&list=PL2_aWCzGMAwI3W_JlcBbtYTwiQSsOTa6P&index=38).

My example implementations of a graph can be found [here]().

Graph Time Complexity:
- ?