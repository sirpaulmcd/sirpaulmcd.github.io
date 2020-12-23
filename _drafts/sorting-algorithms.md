---
layout: default
title: Sorting Algorithms
permalink: /tutorials-cheat-sheets/data-structures-and-algorithms/sorting-algorithms/
parent: Data Structures and Algorithms
grand_parent: Tutorials and Cheat Sheets
has_children: false
nav_order: 3
nav_exclude: false
has_toc: false
---

# Sorting Algorithms

Now that you have a basic understanding of complexity and Big O notation, it's time to learn the fundamental sorting algorithms. These algorithms have already been created for us, we just need to know how and when to use them. There are a great deal of sorting algorithms out there: 

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/sorting-algorithm-selection.png" alt="sorting-algorithm-selection.png"/>
</p>

However, we'll just be learning about the fundamental algorithms you would likely see in a university or junior interview environment. We'll start with the most basic sorting algorithms:
- Selection sort
- Bubble sort
- Insertion sort

Then we'll cover some more useful sorting algoirthms:
- Quick sort
- Merge sort

## Array Sorting Algorithms

For simplicity, we'll be applying these sorting algorithms to arrays. Arrays are linear data structures. As such, sorting algorithms are commonly used on them. Although, the general sorting process is the same for all linear data structures, the exact implementation of the sorting algorithm will differ. For example, the code required to implement insertion sort using an array will differ from the code required to implement insertion sort using a linked list. Therefore, when you are learning these algorithms, it is important that you focus on understanding the general process instead of memorizing the exact implementation. That way, you can implement the sorting algorithm regardless of the underlying data structure.

The time and space complexities of common array sorting algorithms are shown below:

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/array-sorting-complexity-chart.png" alt="array-sorting-complexity-chart.png"/>
  <br />
  <a href="https://www.bigocheatsheet.com">source: bigocheatsheet.com</a>
</p>

From this chart, you can tell that the basic sorting algorithms of bubble, insertion, and selection sort are not very scalable. However, this doesn't mean they are useless. The fundamental algorithms are simple to learn and implement. Therefore, they are a good place to start when learning sorting algorithms. They are also perfectly reasonable to use for applications involving small input sizes. Big O time complexity only tells us that these algorithms will become unreasonably intensive at large input sizes. If we are only sorting arrays with small sizes, it may be more beneficial to use these sorting algorithms due to their simplicity. If you are dealing with large arrays, make sure to use more sophistocated sorting methods like quicksort and mergesort.

While learning the following sorting algorithms, one of the best tools you can use is [visualgo.net](https://visualgo.net/en/sorting). This website allows you to visualize various sorting algorithms for custom arrays. You can go at your own pace working step-by-step through the code. Another good resource is [GeeksForGeeks](https://www.geeksforgeeks.org/sorting-algorithms/). They have a good amount of documentation of each of the sorting algorithms. Their pages include examples as well as implementations in common programming languages.

## Bubble Sort

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/bubble-sort.gif" alt="bubble-sort.gif"/>
  <br />
  <a href="https://visualgo.net/en/sorting">source: visualgo.net</a>
</p>

Bubble sort algorithm steps through the array and swaps an element with its neighbor if it is out of order. This way, the largest unsorted value "bubbles" to the to end of the array on each pass. Since we know that the largest value has been properly sorted, sequential passes are performed using the remaining, unsorted section of the array. This can be seen in the above gif when elements are colored orange after being sorted.

## Insertion Sort

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/insertion-sort.gif" alt="insertion-sort.gif"/>
  <br />
  <a href="https://visualgo.net/en/sorting">source: visualgo.net</a>
</p>

## Selection Sort

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/selection-sort.gif" alt="selection-sort.gif"/>
  <br />
  <a href="https://visualgo.net/en/sorting">source: visualgo.net</a>
</p>

## Quick Sort

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/quick-sort.gif" alt="quick-sort.gif"/>
  <br />
  <a href="https://visualgo.net/en/sorting">source: visualgo.net</a>
</p>

## Merge Sort

<p align="center">
  <img src="/assets/images/data-structures-and-algorithms/sorting-algorithms/merge-sort.gif" alt="merge-sort.gif"/>
  <br />
  <a href="https://visualgo.net/en/sorting">source: visualgo.net</a>
</p>
