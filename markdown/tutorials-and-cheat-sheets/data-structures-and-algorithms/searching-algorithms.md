---
layout: default
title: Searching Algorithms
permalink: /tutorials-cheat-sheets/data-structures-and-algorithms/searching-algorithms/
parent: Data Structures and Algorithms
grand_parent: Tutorials and Cheat Sheets
has_children: false
nav_order: 2
nav_exclude: false
has_toc: false
---

<h1>Searching Algorithms</h1>

### Table of contents:

- [Fundamental Searching Algorithms](#fundamental-searching-algorithms)
  - [Linear (Sequential) Search](#linear-sequential-search)
    - [Description](#description)
    - [Linear search Java implementation](#linear-search-java-implementation)
    - [Complexity](#complexity)
  - [Binary Search](#binary-search)
    - [Description](#description-1)
    - [Iterative binary search Java implementation](#iterative-binary-search-java-implementation)
    - [Recursive binary search Java implementation](#recursive-binary-search-java-implementation)
    - [Complexity](#complexity-1)
- [What next?](#what-next)

# Fundamental Searching Algorithms

When data is stored inside of a data structure, we need some way of locating it later on when it's needed. As such, searching is one of the most common data structure operations. Now that you have a basic understanding of complexity and Big O notation, it's time to learn the fundamental array searching algorithms. Why arrays? Well, arrays are the most simple/common type of data strucutre. More complex data structures are often implemented using arrays. Therefore, knowing how to search an array is an important skill. 

Technically, under the right conditions, these sorting algorithms can be applied to any linear data structure. Therefore, when you are learning these algorithms, it is important to focus on understanding the general process instead of memorizing the exact implementation. That way, you can apply them to other linear data structures in any language regardless of the underlying conditions.

There are two fundamental searching algorithms:
- Linear (AKA sequential) search
- Binary (AKA half-interval or logarithmic) search

If you want to empirically see how the performance of these searching algorithms compare, I have implemented them in java. Using this [script](https://github.com/sirpaulmcd/Data-Structures-And-Algorithms/blob/main/src/searching/SearchingAlgorithms.java), you can record the runtime of each searching algorithm with input arrays of varying orders and sizes. 

## Linear (Sequential) Search

### Description

Linear search is about as basic a searching algorithm can be. It brute-force checks every element for a match. It can be applied to a sorted or unsorted collection. 

The general algorithm is as follows. Given a search key:
- Start at the beginning of the list
- Check the current element to see if it matches the search key
  - If a match is found, return
  - Else, if a match is not found, move on to the next element
- Repeat process until either a match is found or every element has been checked

### Linear search Java [implementation](https://github.com/sirpaulmcd/Data-Structures-And-Algorithms/blob/main/src/searching/SearchingAlgorithms.java)

<script src="https://gist.github.com/sirpaulmcd/f44db8114ad233b63df5da604f865311.js?file=LinearSearch.java"></script>

### Complexity

Time complexity where `n` is the number of elements:

| Average/Worst | Reasoning |
| :-----------: | --------- |
| O(n) | In the average case, a match is found half way through the collection where `(n+1)/2` comparisons have been performed. This simplifies to `O(n)`. In the worst case, a match will not be found and `n` comparisons will be performed. 

Space complexity where `n` is the number of elements:

| All cases | Reasoning |
| :-------: | --------- |
| O(1) | The space complexity of linear search is O(1) because its memory allocations do not depend on input size and no recursive calls are made. |

**Fun fact:** Even though linear search has a worse time complexity than binary search, it can actually out perform binary search when applied to very small collections due to its simplicity.

## Binary Search

### Description
Binary search is significantly more effective/scalable than linear search but it can only be performed on sorted lists.

The general algorithm is as follows. Given a sorted collection and a search key:
- Locate the middle item
  - If a match is found, return
  - Else, if middle item less than key, repeat process on right (i.e. larger) half of the array
  - Else, if middle item greater than key, repeat process on on left (i.e. smaller) half of the array
- Continue until match found or subdivision is no longer possible

This algorithm is often compared to finding a word in a dictionary:
- Navigate to a page half way through the dictionary
  - If your word (i.e. key) is alphabetically lesser than the words on the page, navigate to a page half way between your current page and the beginning
  - If your word is alphabetically greater than the words on the page, nagivate to a page half way between your current page and the end. 
- Repeat this process until you find a match or realize your word does not exist. 
 
Although you may not search a dictionary quite as systematically, the general technique is the same. Just like how your brain may skip to the end of a dicitonary to search for a word starting with the letter Z, optimizations can be made to this algorithm to increase its speed.

Binary search significantly outperforms linear search in almost all cases. As seen by the difference in time complexity, the performance difference increases significantly with larger input sizes. For more information, check out the [GeeksForGeeks documentation]() or the [mycodeschool video tutorials](https://www.youtube.com/watch?v=j5uXyPJ0Pew&list=PL2_aWCzGMAwL3ldWlrii6YeLszojgH77j).

### Iterative binary search Java [implementation](https://github.com/sirpaulmcd/Data-Structures-And-Algorithms/blob/main/src/searching/SearchingAlgorithms.java)

<script src="https://gist.github.com/sirpaulmcd/f44db8114ad233b63df5da604f865311.js?file=BinarySearchIterative.java"></script>

### Recursive binary search Java [implementation](https://github.com/sirpaulmcd/Data-Structures-And-Algorithms/blob/main/src/searching/SearchingAlgorithms.java)

<script src="https://gist.github.com/sirpaulmcd/f44db8114ad233b63df5da604f865311.js?file=BinarySearchRecursive.java"></script>

### Complexity

Time complexity where `n` is the number of elements:

| Average/Worst | Reasoning |
| :-----------: | --------- |
| O(log(n)) | On each step of binary search, the remaining number of keys to be searched is decreased by a factor of 2. This means we are converging on a solution at an exponential rate. As such, it will only take log(n) (base 2) steps to find a match. |  

Space complexity where `n` is the number of elements:

| Iterative | Recursive | Reasoning |
| :-------: | :-------: | --------- |
| O(1) | O(log(n)) | The space complexity of iterative binary search is `O(1)` because its memory allocations do not depend on input size and no recursive calls are made. The space complexity of recursive binary search is `O(log(n))` because constant-space memory allocations are applied to `log(n)` recursive levels. |

Therefore, iterative binary search is typically a better algorithm than recursive binary search due to its advantage of constant space complexity.

# What next? 

Now that you are familiar with searching algorithms, you may want to apply them yourself for practice. If you want to empirically see how the performance of these searching algorithms compare, using this [script](https://github.com/sirpaulmcd/Data-Structures-And-Algorithms/blob/main/src/searching/SearchingAlgorithms.java), you can record the runtime of each searching algorithm with input arrays of varying orders and sizes. When you are comfortable with this section, check out the [data structures](/tutorials-cheat-sheets/data-structures-and-algorithms/data-structures) section.
