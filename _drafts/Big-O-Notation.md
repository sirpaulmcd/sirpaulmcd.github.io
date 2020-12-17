# Big O Notation

## Theory
Big O Notation is just a way to describe how the input size of an algorithm impacts its running time. In other words, it shows how scalable an algoritm is at increasing input sizes. For example, here are the typical Big O runtime categories:
- `O(1) - Constant Time`
- `O(log n) - Logarithmic Time`
- `O(n) - Linear Time`
- `O(n log n) - N Log N Time`
- `O(n<sup>p</sup>) - Polynomial Time`
- `O(k<sup>n</sup>) - Exponential Time`
- `O(n!) - Factorial Time`

Here are the above categories visualized:

<p align="center">
  <img src="https://drive.google.com/uc?export=view&id=12Q-7rP5Ugay-6Et4tloyqGp9gg2T2oDb"/>
  
  <br/>

  [Source](https://www.bigocheatsheet.com/)
</p>

Note that, at this scale, `O(log n)` and `O(1)` appear the same. In reality, `O(1)` is a horizontal line while `O(log n)` is a curve that quickly flattens out into a straight line. This distinction is important to keep in mind. The above image only shows the general shape of the typical Big O functions. The exact values of the curves will differ with each algorithm. You should also keep in mind that there are runtimes slower than O(n!). That's just where the chart cuts off.

Let's translate these relationships into practical examples. If we have a snippet of code that has a `constant` time complexity. It means that, no matter how large the input size is, the same amount of primitive operations will be required to execute the code. Therefore, runtime will be consistent.

If we have a snippet of code that has a `linear` time complexity. We know that runtime will increase linearly with input size. Recall the previous example from the [Complexity Introduction](): 

<p align="center">
    <img src="https://drive.google.com/uc?export=view&id=1IEs2T-VBSgmYqV8LYkbjZDv7WxCjNLqm"/>
</p>

The Big O (i.e. worst case) runtime is `O(8n-2)` where n is the size of the input array. You may notice that this is a linear relationship as it follows the linear formula `y = mx + b`. At very large values of n, the constants `8` and `2` become insignificant and the expression simplifies to `O(n)` complexity.

So why do these relationships matter anyway? Well, software developers use them as a means to compare the performance of different algorithms. If we have two algorithms that can sort an array, but the first has a time complexity of O(n log n) and the second has a time complexity of O(n<sup>2</sup>), we know that the first algorithm will perform much faster for large inputs and is therefore more scalable.

Now that you know the basic reasoning behind the Big O method of ranking code, it's time to jump into some examples. The basic steps for calculating time complexity in terms of Big O are as follows:
- Sum the number of primitive operations line by line
- Use the worst case for conditional statements
- Simplify ending expression

Recall that primitive operations include:
- Accesses (i.e. accessing value from an array) -> `array[i]`
- Arithmetic -> `x + 5`
- Assignments -> `x = 5`
- Comparisons -> `x < 5`
- Returns -> `return x`

## Simple Cases

To get started, we'll be going over how to derive the Big O time complexity for common code that you will see in simple programs.

### Example 1
Let's follow this process on a basic example:

<p align="center">
    <img src="https://drive.google.com/uc?export=view&id=1sZI_TX6jOb831aV1aqErP5Y1bUvV79QM"/>
</p>


To understand the complexity of this algorithm, we can consider how it will be ran on a line-by-line basis.

Line 1:
- Single operation (assignment), independent of input size -> O(1)

Line 2:
- Initialize iterator variable `i`. Happens only once.
- Set a conditional statement. This is checked once for every inner loop iteration PLUS one final check when the conditional equates to false.
  - For example, if `i = 3`, the conditional would be ran when `i = 0, 1, 2, AND 3`.
- Increment `i`. Happens once for every inner loop iteration.

Line 3:
- Three operations (arithmetic, assign, and access). Executed once for every inner loop iteration.

Now that we know the complexity of each line, we sum the time complexity of each line into a formula representing the time complexity of the entire algorithm. In this case, we find that the algorithm has a time complexity of O(5n + 3) which is simplified down to O(n).

Why are the constants dropped for simplicity? At large values of n, these constants become relatively insignificant. Realistically, we're only looking for the simplified Big O notation. That's where the biggest time savings are found. If you are looking to compare two algorithms that fall under the same Big O category, then you'd keep the constants. However, that's only really necessary if you're trying to make sure your algorithms are as optimized as possible (nit-picky).

### Example 2

Let's take it a step further. Instead of one loop, let's see what happens when we nest a second loop inside the first.

<p align="center">
    <img src="https://drive.google.com/uc?export=view&id=1MFV7cr5wyytoo1m_nFTSEJEkcwMYLptk"/>
</p>


Finding the time complexity is very similar to the previous example. The twist is that you have to account for the impact of nesting loops. As we know from the first example, line 1 has a time complexity of O(2n + 2) or O(n). Line 2, being the same loop also has a time complexity of O(2n + 2) or O(n). However,its execution is repeated for each iteration of its overlapping loop. In this case, the loop iterates n times. Therefore, the complexity of line 3 is O((2n + 2) * n) = O(2n<sup>2</sup> + 2n). Summing the time complexity of each line shows us that the overall algorithm has a time complexity of O(5n<sup>2</sup> + 4n + 2) or O(n<sup>2</sup>).

Why was the expression simplified to O(n<sup>2</sup>)? Similarly to the previous example, at large values of n, the rest of the expression becomes negligible. Since the difference between Big O categories are incredible orders of magnitude, it really only matters what ballpark the algorithm is in. As such, we simplify the expression to contain the most significant value.

### Example 2.5

You might be thinking, "This process takes forever!", and you'd be right. Typically, software developers do not calculate time complexities down to the last computation. Practical applications of Big O drop the extra details at the end anyway. However, I felt that knowing the process at a low level would help you better understand the theory.

For the majority of your time using Big O techniques, you will simply be scanning for the "heavy hitters" on each line and their relationships to each other. Let's look at the previous example again and take a more streamlined approach.

<p align="center">
    <img src="https://drive.google.com/uc?export=view&id=14MpnMFLAw4hIGwZE7qpL1-VXcPFd6Peb"/>
</p>


As you can see, the only important lines to consider were lines 1 and 3. Since we know each loop iterates n times, we know that this compounds into a complexity of O(n<sup>2</sup>) for the inner loop. That was much faster!

## Advanced Cases

The above section explored some fundamental cases. However, as you will find, there are many more advanced cases that require some deeper thinking.

### Example 3: The Sum of Integers 1 through N
You may have noticed that we only really learned how to find O(1), O(n), and O(n<sup>k</sup>) complexities. Let's look at another example:

<p align="center">
    <img src="https://drive.google.com/uc?export=view&id=1sqYPq20NpwGMLV2lU0-LbP4mjFAfjnjb"/>
</p>


In this case, the inner `for` loop is executed an additional time for every iteration of the outer loop. When `i = 1`, the inner loop iterates once. When `i = 2`, the inner loop iterates twice. This repeats until `i = n` and the inner loop iterates n times. Therefore, the inner loop iterates the sum of 0 + 1 + 2 + ... + n-1 times. Mathematically, this sum can be simplified to `n(n+2)/2`. 

Don't worry if you didn't already know that. A 10 year old solved it back in the late 1700s. (To be fair, they grew up to be an amazing mathematician and physicist.) If you're not a naturally gifted 10 year old math wizard, you can find an explanation of the proof [here](https://www.youtube.com/watch?v=tpkzn2e5mtI). Using the formula, we can see that the algorithm has a complexity of O(n<sup>2</sup>).

This pattern appears in software frequently enough that having the formula for the sum of 1 to N memorized is a good idea. 

### Example 4: Logarithic complexity

There is another type of `for` loop that you may come across. Instead of incrementing/decrementing after each iteration, it reduces the remaining iterations by a factor. Here's an example:

<p align="center">
    <img src="https://drive.google.com/uc?export=view&id=11rQ442_9QhlOcscn1uhtMDkHX7Kkpgkk"/>
</p>


As you can see, instead of incrementing j, the inner for loop divides j by a factor. When an algorithms steps are reduced by a factor, the resulting complexity is likely O(log n). Think of it this way. The value of `j` starts at `n` and the loop will continue until `j` falls below 1. With every iteration of the inner loop, the value of `j` is halved. Therefore, the value of `j` is converging to a value below 1 at an exponential rate. Inversely, it could be said that the loops runtime (or required computations) grows at a logarithmic rate with increasing values of `n`. Hence the O(log n) time complexity.

### Example 5: Recursive functions

Loops are not the only way code can be compounded multiple times. Recursive functions act in a similar way. Here's an example function used to calculate the factorial value of an integer:

<p align="center">
    <img src="https://drive.google.com/uc?export=view&id=1wGjtledTMAA2dXI8DReHu9P3Wiwv2xqx"/>
</p>


As you can see, this function will be recursively called from `n` until the input value is incremented down to 1. Therefore, this function (complexity of `O(1)`) will be recursively executed `n` times. As such, the time complexity is `O(1) * n = O(n)`.


### Example 6: Exponential runtimes

In some cases, you will see functions that recursively call themselves multiple times over. The previous example only had one recursive call. A popular example of this is the recursive fibonacci method. It returns the `nth` number of the fibonacci sequence. For example, the fibonacci sequence starts as `1, 1, 2, 3, 5, 8, 13, ...`. Therefore, `fibonacci(4)` should yield a result of `3`.

<p align="center">
    <img src="https://drive.google.com/uc?export=view&id=1ehHmvQvHryC2P3-FIs2tytBDcIBDjYoT"/>
</p>


As can be seen, fibonacci(4) will branch off into two fibonacci(3) calls. Each fibonacci(3) call will branch into two more fibonacci(2) calls. This will continue until the fibonacci(1) calls end the cycle. This branching can be visualized like so: 

<p align="center">
    <img src="https://drive.google.com/uc?export=view&id=1sN7o50s2iOwwgWkkZbeD1xBar3z0glxC"/>
</p>


To know how many times this O(1) code is recursively excuted, we must find the number of nodes in this tree. As can be seen, each iteration doubles the number of nodes. Therefore, we know the complexity is exponential because the required operations grows at an exponential rate. When dealing with a tree such as this, the complexity can be represented as O(branches<sup>depth</sup>) where `branches` is the number of branches per node and `depth` is the depths of the tree. In other words, `branches` is the number of recursive calls within the function and `depth` is the maximum number of iterations before the input value reaches the end case. Therefore, since there are 2 recursive calls in the function and it takes `n` iterations for the input value to be decremented to 1, the complexity of this function is O(2<sup>n</sup>).