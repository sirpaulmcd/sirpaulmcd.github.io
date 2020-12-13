# Big O Notation

Big O Notation builds off of the simple example discussed in the [Complexity Introduction](). The basic steps for calculating time complexity in terms of Big O are as follows:
- Sum the number of primitive operations
- Use the worst case for conditional statements
  - Watch for loops that change the number of remaining steps by a factor
- Simplify ending expression
  - Multiply nested loops together and discard loops added in series

Recall that primitive operations include:
- Accesses (i.e. accessing value from an array) -> `array[i]`
- Arithmetic -> `x + 5`
- Assignments -> `x = 5`
- Comparisons -> `x < 5`
- Returns -> `return x`

