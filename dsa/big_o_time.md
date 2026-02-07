# Big-O Time Complexity — Reference Guide

What it is

Big-O describes an upper bound on how an algorithm's runtime grows with input size n. Use Big-O for worst-case reasoning; Omega denotes a lower bound and Theta denotes a tight bound.

Common classes and examples

- O(1) — Constant time
  - Explanation: runtime does not depend on input size.
  - Example: accessing an array element: arr[0]
  - JS: const x = arr[0]; // O(1)

- O(log n) — Logarithmic time
  - Explanation: problem size reduces multiplicatively each step.
  - Example: binary search halves the search space each iteration.
  - JS: binary search loop above // O(log n)

- O(n) — Linear time
  - Explanation: runtime grows proportionally with n.
  - Example: single loop over array.
  - JS: for loop above // O(n)

- O(n log n) — Linearithmic
  - Explanation: often from divide-and-conquer with linear combine step or comparison sorts.
  - Example: merge sort, typical sorting algorithms.
  - JS: arr.sort((a,b)=>a-b) // O(n log n)

- O(n^2) — Quadratic
  - Explanation: nested loops over n produce n * n operations.
  - Example: simple double loop for pairwise comparisons.
  - JS: nested for loops above // O(n^2)

- Exponential and factorial (O(2^n), O(n!))
  - Explanation: algorithms exploring all subsets/permutations.
  - Example: brute-force subset generation or traveling salesman naive search.

Rules to calculate

- Count dominant operations and simplify: drop constants and lower-order terms.
- Addition: sequential steps -> keep the max term.
- Multiplication: nested loops -> multiply.
- Recurrences: form T(n) and use Master Theorem or expansion.
- Amortized: average per operation over sequence (dynamic array push is O(1) amortized).

Recurrence examples

- Merge sort: T(n) = 2T(n/2) + O(n) -> O(n log n).
- Quick sort: average O(n log n), worst-case O(n^2).

Practical tips & checklist

- Identify loops/recursion and write a cost formula.
- Simplify to dominant term; prefer worst-case unless asked otherwise.
- When sorting, include preprocessing cost.
