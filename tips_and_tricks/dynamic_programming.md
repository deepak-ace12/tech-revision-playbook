## Converting Recursion to Dynamic Programming using Matrix

- Define the Problem Dimensions: Create a 2D matrix (or array) of size (n + 1) x (m + 1), where n represents the number of items (or the current index) and m represents the capacity (or other varying parameter).

    - The extra row and column usually represent base cases (like zero-length sequences). For example, in problems like string matching or the longest common subsequence, having an additional row and column can allow you to directly access base cases without special handling.

- Account for Base Cases: The extra +1 space is used to accommodate the base conditions, such as when either the number of items is 0 or the capacity is 0.

- Initialize the Matrix: Fill the matrix with appropriate base case values. For many problems, the 0th row and 0th column should be initialized to 0, representing scenarios where no items are considered or the capacity is zero:

  ```python3
    if capacity == 0 or n == 0:
        return 0
    ```


### Indexing of Items vs. Capacities:
- i (Items): We start i from 1 because the first row of our DP table (i.e., dp[0][...]) corresponds to the case where no items are included. This row is used to initialize the profits when no items are considered. The row representing 0 items (i.e., dp[0][...]) serves as the base case. It tells us that if there are no items to include, the maximum profit for any capacity is 0.
  
- j (Capacities): We can start j from 0 (although we have started it from 1 because we have already initialized the first columns with zeroes) to represent all capacities, including 0. This is necessary to correctly compute profits for scenarios where the capacity of the knapsack is zero.