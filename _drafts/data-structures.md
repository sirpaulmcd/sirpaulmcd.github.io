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
  - Heaps
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

Even with these definitions, the complexities on the above table can be misleading. For example, the `O(1)` insertion time complexity for linked lists assumes that you already have a reference to the node you're inserting after. Typically, when adding/removing data to/from a linked list, a sequential search is required to find the desired position for insertion/deletion. This would make these operations `O(n)`.

In this section, we'll be going over the fundamental data structures. However, descriptions are not enough. I find that the best way to learn how a data structure works is to implement it yourself in your preferred programming language. [GeeksForGeeks](https://www.geeksforgeeks.org/data-structures/) has extensive documentation on data structures. Including sample implementations in a variety of languages. They also have quizzes and practice questions to help you hone your skills. Additionally, [mycodeschool](https://www.youtube.com/user/mycodeschool) is a youtube channel with plenty of quality video tutorials on data structures.

# Arrays (Dynamic)

If you're at the point where you're learning data structures and algorithms, you likely already know what an array is. If not, refer to the [GeeksForGeeks documentation](https://www.geeksforgeeks.org/array-data-structure/) or the [mycodeschool video tutorial](https://www.youtube.com/watch?v=5tPLyHCZdU0).

Arrays are typically primitive data types so they have little functionality out of the box. Primitive arrays can't perform fundamental data structure operations such as `searching`, `inserting`, and `deleting`. Therefore, when "arrays" are compared to other data structures, the comparison typically involves dynamic arrays such as an ArrayList. An ArrayList is essentially just an array that has been extended to perform the fundamental data structure operations.

My example implementation of an ArrayList in Java can be found [here]().

Worst Case Array Time Complexity:
- Indexing - `O(1)`
  - Instantaneous. Given an index, you can immediately find the value.
- Searching - `O(n)`
  - In the worst case, an array must be sequentially searched only to find the value at the last index.
- Inserting - `O(n)`
  - In the worst case, the insertion happens at the first index and all elements must be moved up by one index.
- Deletion - `O(n)`
  - In the worst case, the deletion happens at the first index and all elements must be moved down by one index.

Note that some implementations of dynamic arrays double their size when they reach max capacity. As such, when there is space remaining in the array, insertion complexity is `O(1)`. When there isn't space and the array must be resized, the time complexity is `O(n)`. Having scenarios that result in different time complexities is referred to as `amortized` time complexity.

# Linked Lists


# Stacks

# Queues

https://www.youtube.com/watch?v=okr-XE8yTO8 