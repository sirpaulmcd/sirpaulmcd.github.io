Test

# Complexity

Let's say you have two snippets of code (i.e. algorithms) in front of you. Each snippet performs the same overall function but the methods used are different. If you want to know which one is better in terms of performance/efficiency, complexity can help.

Complexity is a mesaure of software performance in terms of the:
- Time required to execute (Time Complexity)
- Amount of memory required (Space Complexity)
- Number of steps/arithmetic operations required (Computational Complexity)

In terms of Data Structures and Algorithms, depending on the application, time complexity is typically the priority followed by space complexity. Computational complexity is more of a tie-breaker. 

## Why Complexity

So you've got two code snippets and you want to know which is better. Why can't we just run each snippet and see which algorithm runs faster? There are a number of reasons for this:
- Algorithm performance depends on the input. Algorithms may be faster for certain inputs and slower for others. If we are just manually timing the code, performance can't be tested for all possible inputs.
- Algorithm performance depends on the hardware/environment in which it is run. Therefore, algorithm runtimes cannot be compared unless ran using the same device. 
- Both algorithms would need to be fully implemented in order to test/compare using this method.

Complexity addresses these problems because it provides a way to measure the performance of an algorithm for every possible input regardless of programming language or hardware. 

### Time Complexity

Time complexity does so by summing the number of primitive operations and assuming they all take a constant amount of time. Primitive operations include:
- Accesses (i.e. accessing value from an array) -> `array[i]`
- Arithmetic -> `x + 5`
- Assignments -> `x = 5`
- Comparisons -> `x < 5`
- Returns -> `return x`

Let's see an example on a simple algorithm to find the maximum value in a numerical array: 

<p align="center">
    <img src="https://drive.google.com/uc?export=view&id=1IEs2T-VBSgmYqV8LYkbjZDv7WxCjNLqm"/>
</p>

Let's call the functional relationship between the number of operations required to handle an array t(n) where n is the size of the input array.

In the best case scenario, where the maximum value is at the beginning of the array, line 6 is skipped for every following loop. Therefore, only 4 operations take place in each loop cycle. As such, t(n) = 2 + 1 + 2n + **4**(n-1) + 1 = 6n.

If we were to graph this relationship with array size on the x-axis and execution time on the y-axis, we'd get a straight line with a slope of 6:

<p align="center">
    <img src="https://drive.google.com/uc?export=view&id=1dVJlm-bmqcV2kkQvuS9Otoa24Zh7lHAs"/>
</p>

Therefore, for every additional value we add to this array, we're increasing the execution time by 6 operations. 

In the worst case scenario, where the maximum value is at the end of the array, line 6 is never skipped. Therefore, 6 operations take place in each loop cycle and t(n) = 2 + 1 + 2n + **6**(n-1) + 1 = 8n-2. 

In the average case, the maximum value will likely be somewhere mixed in between the first and last element of the array. The resulting performance, therefore, will be somewhere between these two extremes.

With this example (more complex examples are to come), you may now see that algorithm performance depends on the input data! There are 3 function notations used to describe these cases: O, Ω, and Θ.
- O (big O): Upper bound on algorithm execution time.
- Ω (big omega): Lower bound on algorithm execution time.
- Θ (big theta): Both O and Ω simultaneously (unnecessary for tutorial scope).

In industry, the only notation that really matters is Big O. That's because knowing the worst case scenario is the most useful piece of information. Efficient algorithms typically use code that has the minimial "worst case scenario".

### Space Complexity

Space complexity uses a fairly similar technique, although easier to grasp. It accounts for the total number of values stored in memory. For example, an array that stores n values will need O(n) space. Functionally, this means that the required storage space increases linearly with increased array size. Similarly, a 2D array of size n-by-n would require O(n*n) or O(n<sup>2</sup>) space.

Note that stack space required for recursive calls must also be accounted for.

## What next? 

Now that you have a basic understanding of the underlying theory, it's time to dive into the [specifics of Big O notation](). 