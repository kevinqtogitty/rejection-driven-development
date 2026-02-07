# Big-O Space Complexity — Reference Guide

What it is

Space complexity measures how the memory usage of an algorithm grows with input size n.
Distinguish auxiliary space (extra memory beyond input) from total space (includes input storage).

Common classes

- O(1) constant, O(log n), O(n), O(n log n), O(n^2)

How to calculate

- Count newly allocated data structures (arrays, objects, maps) as functions of n.
- Include recursion stack space: depth × per-call memory counts as extra space.
- Ignore input size when reporting auxiliary space; include it for total space if asked.
- Reuse buffers where possible — reused space still counts as O(1) extra if independent of n.

Classes and examples

- O(1) — Constant space
  - Explanation: uses a fixed amount of extra memory regardless of n.
  - Example: swapping two variables, counting with a few scalars.
  - JS: let i = 0, sum = 0; // O(1) aux

- O(log n) — Logarithmic space
  - Explanation: often from recursion stack of divide-and-conquer algorithms.
  - Example: recursion depth for balanced mergesort/quickselect is O(log n).
  - JS: recursive binary search uses O(log n) stack.

- O(n) — Linear space
  - Explanation: memory grows proportionally with n (arrays, maps, result lists).
  - Example: copying an array or storing boolean visited flags.
  - JS: const copy = arr.slice(); // O(n)

- O(n log n), O(n^2)
  - Explanation: less common; e.g., structures with per-node logs or quadratic storage.

Recursion and stack space

- Include recursion depth × per-call memory as extra space.
- Linear recursion depth -> O(n) stack, balanced divide-and-conquer -> O(log n) stack.

Common sources of extra space

- Arrays/objects created proportional to n (maps, sets, result lists).
- Call stack from recursion (depth may be log n for balanced divide-and-conquer, or n for linear recursion).
- Temporary buffers used during operations (merging, copying).

Trade-offs and patterns

- In-place algorithms aim for O(1) auxiliary space (e.g., two-pointer swaps, in-place partitioning).
- Memoization/cache trades space for time: increases space to reduce repeated work.
- Iterative implementations often reduce recursion stack usage.

Practical tips

- Explicitly count per-element allocations: if storing k values per input element, space is O(k*n) -> O(n).
- When sorting, consider whether algorithm is in-place (quicksort average O(log n) stack) or not (merge sort O(n) aux).
- Document whether reported space includes input or is auxiliary.

Checklist for solving

- List all variables and data structures that scale with n.
- Include recursion depth and per-call allocations.
- Simplify by keeping dominant term and dropping constants.
- State whether you mean auxiliary or total space.

- Arrays/objects created proportional to n (maps, sets, result lists).
- Call stack from recursion (depth may be log n for balanced divide-and-conquer, or n for linear recursion).
- Temporary buffers used during operations (merging, copying).

Trade-offs and patterns

- In-place algorithms aim for O(1) auxiliary space (e.g., two-pointer swaps, in-place partitioning).
- Memoization/cache trades space for time: increases space to reduce repeated work.
- Iterative implementations often reduce recursion stack usage.

Practical tips

- Explicitly count per-element allocations: if storing k values per input element, space is O(k*n) -> O(n).
- When sorting, consider whether algorithm is in-place (quicksort average O(log n) stack) or not (merge sort O(n) aux).
- Document whether reported space includes input or is auxiliary.

Checklist for solving

- List all variables and data structures that scale with n.
- Include recursion depth and per-call allocations.
- Simplify by keeping dominant term and dropping constants.
- State whether you mean auxiliary or total space.
