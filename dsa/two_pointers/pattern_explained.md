# Two Pointers — Study Guide

## What it is

A technique that uses two indices (pointers) to scan a sequence and make a
single pass (or near single pass) solution. Best when input is linear (array,
string) and constraints allow O(n) or O(n log n) solutions.

## How to recognize

- Input is a linear sequence and you need to find pairs, windows, or partitions.
- Problems mentioning "sorted" arrays, "sum equals target", "max area",
  "palindrome" or "remove duplicates" often fit.
- Typical hint: brute force is two nested loops — one index can often be
  replaced by a moving pointer.

## Base template (opposite ends)

```javascript
// array must be sorted for classic two-sum/area patterns
function twoPointers(arr, target) {
  let left = 0, right = arr.length - 1;
  while (left < right) {
    const sum = arr[left] + arr[right];
    if (sum === target) return [left, right];
    if (sum < target) left++;
    else right--;
  }
  return null;
}
```

## Fast/slow pointers (same direction)

- Use when detecting cycles, finding middle of linked list, or removing
  elements in-place.
- Classic pattern: fast moves 2x, slow moves 1x.

## How to modify the basic pattern

- If array is unsorted: sort it (O(n log n)) then apply two pointers, or use a
  hash map for exact pairs (O(n)).
- For k-sum (k > 2): sort, fix (k-2) elements, then apply two pointers for the
  remaining two (e.g., 3Sum -> fix one, two-pointer the rest).
- For duplicates: after finding a match, advance pointers while skipping equal
  values to avoid duplicate solutions.
- For constraints that require indices (not values): track original indices
  after sorting (store pairs [value, index]).

## Decision rules (move left vs right)

- Opposite ends (target sum): compare computed value to target — move the
  pointer that will move the value towards the target.
- Expand right to grow sum/range, move left to shrink.
- Fast/slow: advance according to required speed ratio (1x vs 2x).

## Complexity

- Two pointers (single pass): O(n) time, O(1) extra space (ignoring sort).
- Sorting first: O(n log n) time, O(n) or O(1) space depending on sort.

## Quick checklist when solving

- Is the array/string sorted or can be sorted? Use opposite-ends pattern.
- Do I need fixed-size or variable-size range? Use for/while with left/right.
- Are there duplicates to handle? Skip equal elements after processing.
- Do pointers cross? Stop when left >= right (or left > right depending on
  inclusive boundaries).

## Final tips

- Draw pointers and example steps on small inputs.
- Implement the simplest template then adapt for edge cases (empty input,
  single element, duplicates).
- Practice: 2Sum (sorted), 3Sum, container-with-most-water, min-window-substring.
