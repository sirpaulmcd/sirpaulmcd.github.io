---
layout: default
title: Complexity
permalink: /tutorials-cheat-sheets/data-structures-and-algorithms/complexity/
parent: Data Structures and Algorithms
grand_parent: Tutorials and Cheat Sheets
has_children: false
nav_order: 1
nav_exclude: false
has_toc: false
---

# Complexity

Let's say you have two snippets of code (i.e. algorithms) in front of you. Each snippet performs the same overall function but the implementations are different. If you want to know which one is better in terms of performance/efficiency, the concept of complexity is used.

Complexity is a mesaure of algorithm performance in terms of the:
- execution time (Time Complexity)
- required storage space in memory (Space Complexity)
- required number of steps or arithmetic operations (Computational Complexity)

In terms of Data Structures and Algorithms, depending on the application, time complexity is typically the priority followed by space complexity. Computational complexity is more of a tie-breaker. 

## Why Complexity?

Why can't we just run each snippet separately and see which algorithm runs faster? There are a number of reasons for this:
- Algorithm performance depends on the input. Algorithms may be faster for certain inputs and slower for others. If we are just manually timing the code, performance can't be tested for all possible inputs.
- Algorithm performance depends on the hardware/environment in which it is run. Therefore, algorithm runtimes cannot be compared unless ran using the same device. 
- Both algorithms would need to be fully implemented in order to test/compare using this method.

Complexity addresses these problems because it provides a way to measure the performance of an algorithm for every possible input regardless of implementation or hardware. 

## Time Complexity

Time complexity addresses the above issues by summing the number of primitive operations and assuming they all take a constant amount of time. Primitive operations include:
- Accesses (i.e. accessing value from an array) -> `array[i]`
- Arithmetic -> `x + 5`
- Assignments -> `x = 5`
- Comparisons -> `x < 5`
- Returns -> `return x`

Let's see an example of this method on a simple algorithm to find the maximum value in a numerical array: 

<p align="center">
    <img src="/assets/images/data-structures-and-algorithms/complexity-and-big-o/complexity-example-1.png" alt="complexity-example-1.png"/>
</p>

Let's call the functional relationship between the number of operations required to handle an array `t(n)` where `n` is the size of the input array.

In the best case scenario, where the maximum value is at the beginning of the array, line 6 is skipped for every following loop. Therefore, only 4 operations take place in each iteration of the loop. As such:

<p align="center">t(n) = 2 + 1 + 2n + <ins><strong>4</strong></ins>(n-1) + 1 = 6n</p>

If we were to graph this relationship, we'd get a straight line with a slope of 6:

<p align="center">
    <img src="/assets/images/data-structures-and-algorithms/complexity-and-big-o/time-complexity-graph.png" alt="time-complexity-graph.png"/>
</p>

Therefore, for every additional value we add to this array, we're increasing the execution time by 6 primitive operations. 

In the worst case scenario, where the maximum value is at the end of the array, line 6 is never skipped. Therefore, 6 operations take place in each iteration of the loop. As a result: 

<p align="center">t(n) = 2 + 1 + 2n + <ins><strong>6</strong></ins>(n-1) + 1 = 8n-2</p>

In the average case, the maximum value will likely be somewhere in between the first and last element of the array. The resulting performance, therefore, will be somewhere between the best and the worst case.

From this example (more complex examples are to come), you should see how algorithm performance is dependent on the input. In the above example, the size of the input array incluenced the execution time of the algorithm. The potential order of numbers within the array resulted in best and worst case execution times. There are 3 notations used to describe these execution times: O, Ω, and Θ.
- O (big O): Upper bound on algorithm execution time.
- Ω (big omega): Lower bound on algorithm execution time.
- Θ (big theta): Both O and Ω simultaneously (unnecessary for tutorial scope).

In industry, the only notation that really matters is Big O. That's because the worst case scenario is the most useful piece of information. Efficient algorithms typically use code that has the minimial "worst case scenario".

## Space Complexity

Space complexity uses a fairly similar technique, although easier to grasp. It accounts for the total number of values stored in memory. For example, an array that stores n values will need O(n) space. Functionally, this means that the required storage space increases linearly with increased array size. Similarly, a 2D array of size n-by-n would require O(n*n) or O(n<sup>2</sup>) space.

Note that stack space required for recursive calls must also be accounted for. More examples will be discussed in the Data Structures section.

## What next? 

Now that you have a basic understanding of the underlying theory, it's time to dive into the specifics of [Big O notation](/tutorials-cheat-sheets/data-structures-and-algorithms/big-o-notation). 