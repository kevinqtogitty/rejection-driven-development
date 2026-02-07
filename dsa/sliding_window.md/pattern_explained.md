# Sliding Window — Study Guide

## What it is

A pattern that maintains a variable-size (or fixed-size) contiguous window over
a sequence and adjusts its bounds to satisfy conditions while scanning the input.

## How to recognize

- Problems ask for longest/shortest contiguous subarray or substring meeting a condition (sum >= target, at most k distinct, no repeats).
- Brute force is typically nested loops that check every subarray — sliding window reduces this to linear by expanding and contracting bounds.

## Base template (variable window)

```javascript
function minSubarrayLen(nums, target) {
  let left = 0, sum = 0, minLen = Infinity;
  for (let right = 0; right < nums.length; right++) {
    sum += nums[right];
    while (sum >= target) {
      minLen = Math.min(minLen, right - left + 1);
      sum -= nums[left++];
    }
  }
  return minLen === Infinity ? 0 : minLen;
}
```

## Fixed-size window

```javascript
function maxSubarraySumK(nums, k) {
  let sum = 0;
  for (let i = 0; i < k; i++) sum += nums[i];
  let maxSum = sum;
  for (let i = k; i < nums.length; i++) {
    sum += nums[i] - nums[i - k];
    maxSum = Math.max(maxSum, sum);
  }
  return maxSum;
}
```

## Common variants

- At most k distinct / no repeats: track frequencies with a map and shrink window when constraints violated.
- Exact sum/target: expand until >= target (or match), then shrink.
- Longest with condition: expand to grow, shrink to restore invariants and record best.

## How to adapt

- Use a map/object to track counts or aggregate data inside the window.
- When duplicates or distinct counts matter, maintain a counter of unique keys.
- Combine with two-pointer opposites when array is sorted and pairs are needed.

## Complexity

- Time: O(n) typically, since each element is visited by right and left at most once.
- Space: O(1) to O(k) depending on additional structures (maps, frequency tables).

## Quick checklist

- Identify expanding pointer (right) and contracting pointer (left).
- Decide what to track inside window (sum, counts, characters).
- Update answer when invariants satisfied.
- Move left until invariants restored.

## Practice problems

- Minimum Size Subarray Sum, Longest Substring Without Repeating Characters, Fruit Into Baskets, Sliding Window Maximum.
