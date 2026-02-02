# Two Sum Sorted ![https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/](LeetCode 167)

## Optimized 0(n)

```javascript
// nums is 1 INDEXED
function twoSum(nums, target) {
  // Use two pointers, 1 on each end
  // If its sorted from low -> high we know if the sum is
  // a. greater than the target we need to move the end pointer
  // b. down to the next smallest value, vice versa until the sum equals the target
  let start = 0, end = numbers.length - 1

  while (start < end) {
    const computed = numbers[start] + numbers[end]
  
    if (computed === target) return [ start + 1, end + 1 ]
    if (computed < target) {
        start++
    } else {
        end--
    }
  }

   return []
}
```
