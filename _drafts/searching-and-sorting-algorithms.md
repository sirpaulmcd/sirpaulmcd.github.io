---
layout: default
title: Searching and Sorting Algorithms
permalink: /tutorials-cheat-sheets/data-structures-and-algorithms/searching-and-sorting-algorithms/
parent: Data Structures and Algorithms
grand_parent: Tutorials and Cheat Sheets
has_children: false
nav_order: 3
nav_exclude: false
has_toc: false
---

<h1>Searching and Sorting Algorithms</h1>

Now that you have a basic understanding of complexity and Big O notation, it's time to learn the fundamental searching and sorting algorithms. These algorithms have already been discovered for us, we just need to know how and when to use them. 

The searching and sorting algorithms covered in this section can be applied to linear data structures. For simplicity, we'll be applying these algorithms to arrays because they are the simplest linear data structure. Although, the general process is the same for all linear data structures, the exact implementation of the algorithms will differ depending on the programming language and applied data structure. Therefore, when you are learning these algorithms, it is important to focus on understanding the general process instead of memorizing the exact implementation. That way, you can implement the searching and sorting algorithms regardless of the underlying conditions.

# Searching algorithms

When data is stored inside of a data structure, we need some way of locating it when it is needed. As such, searching is one of the most common data structure operations. There are two major linear searching algorithms:
- Sequential (AKA linear) search
- Binary (AKA interval) search

## Sequential (Linear) Search

Sequential search is about as basic a sorting algorithm can be. It essentialy brute-force checks every element for a match. It can be applied to a sorted or unsorted collection. Given a search key, sequential search:
- Starts at the beginning of the list
- Compares each successive item to see if it matches the search key
- Continue until match found or reach end of list

Time complexity
- Average/worst case: O(n) (i.e. average case: match found half way where (n + 1)/2 comparisons performed, worst case: match not found, entire list checked)

Even though it has a worse time complexity, sequential search can actually out perform binary search when applied to very small collections (about 20 elements).

## Binary Search

Binary search is more effective than sequantial search but it can only be performed on sorted lists. It is often paralleled to looking in a dictionary for a word. Open a page half way through the dictionary. If your word (i.e. key) is alphabetically lesser than the words on the page, open a page half way between your current page and the beginning and repeat until you find a match. Although, you may not search a dictionary quite as systematically, the general technique is the same. Given a search key, binary search:
- Locates the middle item
  - If match found, return
  - Else if middle item less than key, divide array in half and repeat process on right (i.e. larger) half
  - Else if middle item greater than key, divide array in half and repeat process on on left (i.e. smaller) half
- Continue until match found or subdivision is no longer possible

Time complexity
- Average/worst case: O(log(n)) (each divsion of the array divides the remaining elments to be searched by a factor of 2)

Binary search significantly outperforms linear search for small and larger collections. As the time complexity suggests, the performance difference increases significantly with larger input sizes. For more information, check out the [GeeksForGeeks documentation]() or the [mycodeschool video tutorials](https://www.youtube.com/watch?v=j5uXyPJ0Pew&list=PL2_aWCzGMAwL3ldWlrii6YeLszojgH77j).

# Sorting Algorithms

As you likely already know, sorting is the arrangement of elements within a collection into increasing or decreasing order of some property. There are many scenarios where a developer may want a collection sorted. One of the biggest advantages of having a sorted collection is that you can perform a binary search to find values which can make an algorithm significantly more scalable/efficient. 

Sorting terminology:
- In-place sort:
  - A sort that swaps data within the existing data structure without using extra memory (i.e. uses constant `O(1)` memory). We want our sorting algorithms to be in-place wherever possible.
- Stable sort:
  - A sort that preserves the relative order of eqivalent elements. That is to say, if two elements of equal value exist in a certain order before sorting, they will remain in the same order after sorting.
- Internal sort:
  - A sort where data is kept in primary memory (i.e. in RAM using arrays)
- External sort:
  - A sort where data is kept in secondary memory (i.e. on disk or tape)

In addition to the above terminology, sorting algorithms can also be labelled as either "recursive" or "non-recursive" depending on whether their implementations use recursion. For more information, see the [mycodeschool video tutorial](https://www.youtube.com/watch?v=pkkFqlG0Hds&list=PL2_aWCzGMAwKedT2KfDMB9YA5DgASZb3U&index=1).

There are a great deal of sorting algorithms out there: 

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/sorting-algorithm-selection.png" alt="sorting-algorithm-selection.png"/>
</p>

However, we'll just be learning about the fundamental algorithms you would likely see in a university or junior interview environment. We'll start with the most basic sorting algorithms:
- Selection sort
- Bubble sort
- Insertion sort

Then we'll cover some more useful sorting algoirthms:
- Merge sort
- Quick sort
- Heap sort?

## Array Sorting Algorithms

The time and space complexities of common array sorting algorithms are shown below:

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/array-sorting-complexity-chart.png" alt="array-sorting-complexity-chart.png"/>
  <br />
  <a href="https://www.bigocheatsheet.com">source: bigocheatsheet.com</a>
</p>

From the above chart, using your Big O knowledge, you should be able to tell that the basic sorting algorithms of bubble, insertion, and selection sort are not very scalable due to their `O(n^2)` average/worst case runtimes. However, this doesn't mean they are useless. The basic sorting algorithms are simple to learn and implement. Therefore, they are a good place to start when learning sorting algorithms. Although they are not scalable for large collections, they are perfectly reasonable to use when sorting relatively small collections. In some cases, they may be more beneficial to use due to their simplicity and ease of implementation.

I find that the best way to learn a sorting algorithm is to implement it yourself in your preferred programming language. If you are a visual learner, one of the best tools you can use is [visualgo.net](https://visualgo.net/en/sorting). This website allows you to visualize various sorting algorithms for custom arrays. You can go at your own pace working step-by-step through the code. Another good resource is [GeeksForGeeks](https://www.geeksforgeeks.org/sorting-algorithms/). They have a good amount of documentation of each of the sorting algorithms. Their pages include examples as well as implementations in common programming languages. Additionally, [mycodeschool](https://www.youtube.com/user/mycodeschool) is a YouTube channel with plenty of high quality video tutorials on sorting algorithms.

## Selection Sort

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/selection-sort.gif" alt="selection-sort.gif"/>
  <br />
  <a href="https://visualgo.net/en/sorting">source: visualgo.net</a>
</p>

Insertion sort is often related to sorting a hand of playing cards. The algorithm is as follows:
- Start with all the cards in your right hand (i.e. unsorted array).
- Select the minimum card and place it into your left hand (i.e. sorted array).
- Repeat until all cards have moved from your unsorted right hand to your sorted left hand. 

In terms of software implementation, your left hand represents the original unsorted array and your right hand represents a sorted array. This can be implemented using two separate arrays. However, that would make the space complexity of the algorithm `O(n)`. Ideally, we want our sorting algorithms to be in-place with constant `O(1)` space complexity. Therefore, instead of using 2 arrays, we can simply swap elements around to create sorted/unsorted subsections within the original array. For more information, see the [mycodeschool video tutorial](https://www.youtube.com/watch?v=GUDLRan2DWM&list=PL2_aWCzGMAwKedT2KfDMB9YA5DgASZb3U&index=2).

Selection sort [implementation]() in java:
<p align="center">
  <img src="" alt="selection-sort-implementation.png"/>
</p>

Time complexity of selection sort where `n` is the number of elements:

| Best | Average | Worst | Reasoning |
| :--: | :-----: | :---: | --------- |
| Ω(n<sup>2</sup>) | Θ(n<sup>2</sup>) | O(n<sup>2</sup>) | For every element in the array, the unsorted subarray must be sequentially searched for the minimum value. An `O(n)` search repeated `n` times results in an `O(n^2)` runtime. If the array is already sorted, this process still takes place. |

Space complexity of selection sort is `O(1)` because it can be implemented as an in-place sort.

## Bubble Sort

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/bubble-sort.gif" alt="bubble-sort.gif"/>
  <br />
  <a href="https://visualgo.net/en/sorting">source: visualgo.net</a>
</p>

Bubble sort algorithm steps through the array and swaps an element with its neighbor if it is out of order. This way, the largest unsorted value "bubbles" to the to end of the array on each pass. Since we know that the largest value has been properly sorted, additional passes are performed using the remaining, unsorted subsection of the array. This can be seen in the above gif when elements are colored orange after being sorted. For more information, see the [mycodeschool video tutorial](https://www.youtube.com/watch?v=Jdtq5uKz-w4&list=PL2_aWCzGMAwKedT2KfDMB9YA5DgASZb3U&index=3).

Selection sort [implementation]() in java:

<p align="center">
  <img src="" alt="bubble-sort-implementation.png"/>
</p>

Time complexity of bubble sort where `n` is the number of elements:

| Best | Average | Worst | Reasoning |
| :--: | :-----: | :---: | --------- |
| Ω(n) | Θ(n<sup>2</sup>) | O(n<sup>2</sup>) | In the best case, the array is already sorted and bubble sort only traverses once. In the worst case, the array is in descending order and an `O(n)` bubble traversal occurs for every element in the array (i.e. `n` times). |

Space complexity of bubble sort is `O(1)` because it can be implemented as an in-place sort.

## Insertion Sort

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/insertion-sort.gif" alt="insertion-sort.gif"/>
  <br />
  <a href="https://visualgo.net/en/sorting">source: visualgo.net</a>
</p>

Insertion sort is the last and most efficient of the 3 basic sorting algorithms. Insertion sort can be visualized with a deck of playing cards similar to selection sort: 
- Start with all the cards in your right hand. (i.e. unsorted subarray).
- Select a card and place it into your left hand into the proper sorted position. (i.e. sorted subarray).
- Repeat until all cards have moved from your unsorted right hand to your sorted left hand. 

In terms of software implementation, to remove a card from the unsorted subarray, you simply:
- Store the first element of the unsorted array in a temporary variable.
- Increment the index of its previous neighbors in the sorted subarray until the correct insertion index is made vacant.
- Insert the stored element into the vacant, sorted position.

For more information, see the [mycodeschool video tutorial](https://www.youtube.com/watch?v=i-SKeOcBwko&list=PL2_aWCzGMAwKedT2KfDMB9YA5DgASZb3U&index=4).

Insertion sort [implementation]() in java:

<p align="center">
  <img src="" alt="insertion-sort-implementation.png"/>
</p>

Time complexity of insertion sort where `n` is the number of elements:

| Best | Average | Worst | Reasoning |
| :--: | :-----: | :---: | --------- |
| Ω(n) | Θ(n<sup>2</sup>) | O(n<sup>2</sup>) | In the best case, the array is already sorted and insertion sort only traverses once. In the worst case, the array is in descending order and an `O(n)` neighbor incrementation traversal occurs for every element in the array (i.e. `n` times). |

Space complexity of insertion sort is `O(1)` because it can be implemented as an in-place sort.

## Merge Sort

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/merge-sort.gif" alt="merge-sort.gif"/>
  <br />
  <a href="https://visualgo.net/en/sorting">source: visualgo.net</a>
</p>

In the previous sorting algorithms, the array was sorted by dividing the array into "sorted" and "unsorted" subsections. Merge sort takes a different approach because it is a recrusive algorithm. An overly simplified approximation of the recursive algorithm can be described like so:
- Split the array in half
- Sort the two smaller arrays
- Merge the two sorted smaller arrays back into a single sorted array

The above algorithm is overly simplistic because recursion actually removes the need for the second step. Since the algorithm is recursive, the array is actually divided until there are `n` subarrays that consist of a single element. Since a subarray of one element is already sorted, each subarray is then recursively merged back together such that they are in sorted order. A good visualization of this process can be seen here:

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/merge-sort-visualization.png" alt="merge-sort-visualization.png"/>
  <br />
  <a href="https://www.geeksforgeeks.org/merge-sort/">source: GeeksForGeeks</a>
</p>

Merge sort is a stable sort algorithm. For more information, see the [mycodeschool video tutorial](https://www.youtube.com/watch?v=TzeBrDU-JaY&list=PL2_aWCzGMAwKedT2KfDMB9YA5DgASZb3U&index=5).

Merge sort [implementation]() in java:

<p align="center">
  <img src="" alt="merge-sort-implementation.png"/>
</p>

Time complexity of merge sort where `n` is the number of elements:

| Best | Average | Worst | Reasoning |
| :--: | :-----: | :---: | --------- |
| Ω(n log(n)) | Θ(n log(n)) | O(n log(n)) | Since merge sort divides the array by a factor of 2 in every recursive step, division until we have reached a single element will take `log(n)` (base 2) recusive levels. On each recursive level, all `n` elements are traversed when merging subarrays. |

Space complexity of insertion sort is `O(n)` because, at the last step of the recursive process, the `merge()` uses merges two temporary subarrays (of collective size `n`) into the final sorted array of size `n`.

## Quick Sort

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/quick-sort.gif" alt="quick-sort.gif"/>
  <br />
  <a href="https://visualgo.net/en/sorting">source: visualgo.net</a>
</p>

Similar to merge sort, quick sort is also recursive. Unlike marge sort, quick sort is a non-stable sorting algorithm. However, quick sort is an in-place sort which gives it an advantage in terms of space complexity. You may notice that it has a worst case time complexity of `O(n^2)`. However, this case is almost never seen using randomized quick sort where the "pivot" is selected at random. Quick sort is actually such a practical choice for an efficient sorting algorithm that programming libraries typically implement it for generic sorting functions. The algorithm is as follows:
- Select random element to be the pivot and swap to last index position
- Rearrange the list such that all elements lesser than the pivot are to the left of the pivot and all elements greater than the pivot are to the right (doesn't have to be sorted).
- Split elements to left and right of the pivot into subarrays
- Recursively repeat process until subarrays only contain one element
- Recursive stack of subarrays now represents a binary tree where each pivot represents a node. As a result, the lowest left node will have the lowest value and the lowest right node will have the highest value. Working up the recursive stack using in-order binary tree traversal will yield a sorted array.

For more information, see the [mycodeschool video tutorial](https://www.youtube.com/watch?v=COk73cpQbFQ&list=PL2_aWCzGMAwKedT2KfDMB9YA5DgASZb3U&index=7).

Quick sort [implementation]() in java:

<p align="center">
  <img src="" alt="merge-sort-implementation.png"/>
</p>

Time complexity of quick sort where `n` is the number of elements:

| Best | Average | Worst | Reasoning |
| :--: | :-----: | :---: | --------- |
| Ω(n log(n)) | Θ(n log(n)) | O(n<sup>2</sup>) | In the best/average case, partitioning is balanced such that left and right subarrays are of relatively equal size. If the subarrays are near equal size, quick sort divides the array by approximately a factor of 2 on each recursive step. As such, division until we have reached a single element will take `log(n)` (base 2) recusive levels. On each recursive level, the remaining elements are sequentially traversed (`O(n)` operation) when arranging around the pivot. In the worst case, partitioning is always unbalanced (i.e. the pivot is always the largest element in the array) and only left subarrays are created during the recursive process. As such, division until we have reached a single element will take `n` recursive levels. On each recursive level, the remaining elements are sequentially traversed (`O(n)` operation) when arranging around the pivot.

Space complexity of quick sort:
| Best | Average | Worst | Reasoning |
| :--: | :-----: | :---: | --------- |
| Ω(log(n)) | Θ(log(n)) | O(n) | Since quick sort is an in-place sort is does not require the use of additional data structures. However, since it is a recursive algorithm, additional space is required to account for the rectursive levels necessary to complete the sort. That is why the space complexity corresponds with time complexity in this case. |

# What next? 

There are many more [sorting algorithms](https://www.geeksforgeeks.org/sorting-algorithms/). I will probably add more such as heap, radix, and counting sort to this page eventually. The rest will be up to you as you face more specialized software problems. When you are comfortable with this section, check out the [next](/tutorials-cheat-sheets/data-structures-and-algorithms/) section.
